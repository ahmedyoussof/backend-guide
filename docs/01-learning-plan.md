# Backend Developer Learning Plan
## Evolutionary Approach: Monolith to Microservices

## Project Overview: E-Commerce System
An e-commerce system that will evolve from a monolith to microservices architecture.

### Core Features
- Order processing
- Inventory management
- Shopping cart
- Payment processing
- User management
- Product catalog with search
- Notifications

### Technical Stack
- Java 17+
- Spring Boot 3.x
- PostgreSQL
- Redis (for caching)
- Elasticsearch (for search)
- RabbitMQ (for events)

## Phase 1: Monolithic Foundation (Weeks 1-8)

### Week 1-2: Project Setup and Core Models
#### Focus:
- Basic Spring Boot setup
- Entity design
- Repository layer
- Service layer basics

#### Implementation:
```java
// Example basic entity
@Entity
@Table(name = "orders")
public class Order {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    @ManyToOne
    private User customer;
    
    @OneToMany(cascade = CascadeType.ALL)
    private List<OrderItem> items = new ArrayList<>();
    
    @Enumerated(EnumType.STRING)
    private OrderStatus status;
    
    private BigDecimal totalAmount;
    
    // Basic getters and setters
}

// Example service
@Service
@Transactional
public class OrderService {
    private final OrderRepository orderRepository;
    private final UserRepository userRepository;
    
    public Order createOrder(OrderRequest request) {
        User customer = userRepository.findById(request.customerId())
            .orElseThrow(() -> new UserNotFoundException());
            
        Order order = new Order();
        order.setCustomer(customer);
        order.setItems(mapItems(request.items()));
        order.setStatus(OrderStatus.CREATED);
        order.setTotalAmount(calculateTotal(request.items()));
        
        return orderRepository.save(order);
    }
}
```

### Week 3-4: Basic Web Layer and Validation
#### Focus:
- REST controllers
- Request/Response DTOs
- Input validation
- Basic error handling

#### Implementation:
```java
@RestController
@RequestMapping("/api/orders")
public class OrderController {
    private final OrderService orderService;
    
    @PostMapping
    public ResponseEntity<OrderDTO> createOrder(
        @Valid @RequestBody OrderRequest request
    ) {
        Order order = orderService.createOrder(request);
        return ResponseEntity.ok(OrderMapper.toDTO(order));
    }
    
    @GetMapping("/{id}")
    public ResponseEntity<OrderDTO> getOrder(@PathVariable Long id) {
        Order order = orderService.getOrder(id);
        return ResponseEntity.ok(OrderMapper.toDTO(order));
    }
}

@ControllerAdvice
public class GlobalExceptionHandler {
    @ExceptionHandler(UserNotFoundException.class)
    public ResponseEntity<ErrorResponse> handleUserNotFound(
        UserNotFoundException ex
    ) {
        return ResponseEntity
            .status(HttpStatus.NOT_FOUND)
            .body(new ErrorResponse(ex.getMessage()));
    }
}
```

### Week 5-6: Data Access and Caching
#### Focus:
- JPA repositories
- Query optimization
- Redis caching
- Database indexing

#### Implementation:
```java
@Repository
public interface ProductRepository 
    extends JpaRepository<Product, Long> {
    
    @Query("SELECT p FROM Product p WHERE p.category = :category")
    List<Product> findByCategory(
        @Param("category") Category category
    );
    
    @Cacheable(value = "products", key = "#id")
    Optional<Product> findById(Long id);
}

@Configuration
@EnableCaching
public class CacheConfig {
    @Bean
    public RedisCacheManager cacheManager(
        RedisConnectionFactory factory
    ) {
        RedisCacheConfiguration config = 
            RedisCacheConfiguration.defaultCacheConfig()
                .entryTtl(Duration.ofMinutes(10));
                
        return RedisCacheManager.builder(factory)
            .cacheDefaults(config)
            .build();
    }
}
```

### Week 7-8: Search and Basic Event Handling
#### Focus:
- Elasticsearch integration
- Basic event publishing
- Simple async processing

#### Implementation:
```java
@Service
public class ProductSearchService {
    private final ElasticsearchOperations operations;
    
    public List<Product> searchProducts(String query) {
        NativeSearchQuery searchQuery = new NativeSearchQueryBuilder()
            .withQuery(QueryBuilders.multiMatchQuery(query)
                .field("name", 2.0f)
                .field("description")
                .type(MultiMatchQueryBuilder.Type.BEST_FIELDS))
            .build();
            
        return operations.search(searchQuery, Product.class)
            .getSearchHits()
            .stream()
            .map(SearchHit::getContent)
            .collect(Collectors.toList());
    }
}

@Service
public class OrderEventPublisher {
    private final ApplicationEventPublisher publisher;
    
    public void publishOrderCreated(Order order) {
        publisher.publishEvent(new OrderCreatedEvent(order));
    }
}
```

## Phase 2: Enhancing the Monolith (Weeks 9-14)

### Week 9-10: Domain Events and CQRS
#### Focus:
- Introducing domain events
- Command/Query separation
- Event handlers

#### Implementation:
```java
public abstract class AggregateRoot {
    private final List<DomainEvent> domainEvents = new ArrayList<>();
    
    protected void registerEvent(DomainEvent event) {
        domainEvents.add(event);
    }
    
    public List<DomainEvent> getDomainEvents() {
        return Collections.unmodifiableList(domainEvents);
    }
}

public class Order extends AggregateRoot {
    public void place() {
        validateState();
        this.status = OrderStatus.PLACED;
        registerEvent(new OrderPlacedEvent(this.id));
    }
}

@Service
public class OrderCommandService {
    public OrderId placeOrder(PlaceOrderCommand command) {
        Order order = new Order(command.getOrderLines());
        order.place();
        repository.save(order);
        return order.getId();
    }
}
```

### Week 11-12: Bounded Contexts
#### Focus:
- Identifying domains
- Context mapping
- Anti-corruption layers

#### Implementation:
```java
// Order Context
package com.ecommerce.order.domain;

public class Order extends AggregateRoot {
    private OrderId id;
    private CustomerId customerId;
    private Money totalAmount;
    private OrderStatus status;
}

// Inventory Context
package com.ecommerce.inventory.domain;

public class Stock {
    private ProductId productId;
    private Quantity quantity;
    
    public void reserve(Quantity amount) {
        if (!hasEnoughStock(amount)) {
            throw new InsufficientStockException();
        }
        this.quantity = this.quantity.subtract(amount);
    }
}
```

### Week 13-14: Service Layer Refactoring
#### Focus:
- Application services
- Domain services
- Infrastructure services

#### Implementation:
```java
// Application Service
@Service
public class OrderApplicationService {
    private final OrderRepository repository;
    private final OrderDomainService domainService;
    private final PaymentService paymentService;
    
    @Transactional
    public OrderId placeOrder(PlaceOrderCommand cmd) {
        Order order = repository.findById(cmd.orderId())
            .orElseThrow(OrderNotFoundException::new);
            
        domainService.validateOrder(order);
        paymentService.processPayment(order);
        
        order.place();
        repository.save(order);
        return order.getId();
    }
}

// Domain Service
@Service
public class OrderDomainService {
    public void validateOrder(Order order) {
        if (order.isEmpty()) {
            throw new InvalidOrderException("Order must have items");
        }
        if (!order.hasValidPaymentMethod()) {
            throw new InvalidOrderException("Invalid payment method");
        }
    }
}
```

## Phase 3: Transition to Microservices (Weeks 15-20)

### Week 15-16: Service Discovery and Gateway
#### Focus:
- Spring Cloud setup
- Service registry
- API gateway
- Load balancing

#### Implementation:
```java
// Service Discovery
@SpringBootApplication
@EnableEurekaServer
public class DiscoveryServiceApplication {
    public static void main(String[] args) {
        SpringApplication.run(DiscoveryServiceApplication.class, args);
    }
}

// API Gateway
@SpringBootApplication
@EnableDiscoveryClient
public class GatewayApplication {
    @Bean
    public RouteLocator customRouteLocator(
        RouteLocatorBuilder builder
    ) {
        return builder.routes()
            .route("order_service", r -> r
                .path("/api/orders/**")
                .uri("lb://order-service"))
            .route("product_service", r -> r
                .path("/api/products/**")
                .uri("lb://product-service"))
            .build();
    }
}
```

### Week 17-18: First Microservice Extraction
#### Focus:
- Extract Order service
- Event-driven communication
- Database per service

#### Implementation:
```java
// Order Service
@SpringBootApplication
@EnableDiscoveryClient
public class OrderServiceApplication {
    @Bean
    public CommandGateway commandGateway() {
        return CommandGateway.builder()
            .eventStore(eventStore())
            .eventBus(eventBus())
            .build();
    }
}

// Event Communication
@Service
public class OrderEventHandler {
    @EventListener
    public void on(OrderCreatedEvent event) {
        // Update read model
        // Notify other services
    }
}
```

### Week 19-20: Deployment and Monitoring
#### Focus:
- Docker setup
- Basic Kubernetes
- Monitoring
- Distributed tracing

#### Implementation:
```yaml
# Docker Compose
version: '3.8'
services:
  discovery-service:
    build: ./discovery-service
    ports:
      - "8761:8761"
      
  order-service:
    build: ./order-service
    depends_on:
      - discovery-service
    environment:
      SPRING_PROFILES_ACTIVE: docker
```

## Evolution Strategy
1. Start with clean monolith
2. Introduce DDD concepts gradually
3. Identify service boundaries
4. Extract services one by one
5. Add infrastructure gradually

## Key Principles
- Start simple
- Evolve gradually
- Maintain functionality
- Test thoroughly
- Monitor performance

## Success Metrics
- Code maintainability
- Test coverage
- Response times
- System availability
- Deployment frequency
