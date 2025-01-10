# Backend Learning Resources
Aligned with evolutionary approach from monolith to microservices and senior development practices

## Phase 1: Monolithic Foundation (Weeks 1-8)

### Week 1-2: Project Setup and Modern Development Practices
#### Official Documentation
- [Spring Boot Reference](https://docs.spring.io/spring-boot/docs/current/reference/html/) - Core concepts and setup
- [Git Advanced Operations](https://git-scm.com/book/en/v2) - Advanced git workflows
- [Trunk Based Development](https://trunkbaseddevelopment.com/) - Modern branching strategy

#### Tutorials and Guides
- [Feature Flag Implementation](https://martinfowler.com/articles/feature-toggles.html) - Martin Fowler's guide
- [Code Review Best Practices](https://google.github.io/eng-practices/review/) - Google's Engineering Practices
- [Technical Debt Assessment](https://martinfowler.com/bliki/TechnicalDebt.html) - Understanding and managing debt

#### Example Projects
- [Spring PetClinic](https://github.com/spring-projects/spring-petclinic) - Reference application
- [Feature Flag Sample](https://github.com/ff4j/ff4j) - Feature toggle framework

### Week 3-4: Core Models and Advanced Data Management
#### Official Documentation
- [Spring Data JPA](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/) - Database operations
- [Hibernate Performance Guide](https://docs.jboss.org/hibernate/orm/current/performance/html_single/Hibernate_Performance_Guide.html) - Query optimization
- [Redis Enterprise](https://redis.com/redis-enterprise/technology/redis-enterprise-documentation/) - Advanced caching

#### Tutorials and Guides
- [Database Indexing Strategies](https://use-the-index-luke.com/) - Deep dive into indexing
- [Polyglot Persistence](https://martinfowler.com/bliki/PolyglotPersistence.html) - Multi-database architecture
- [Connection Pooling](https://github.com/brettwooldridge/HikariCP) - HikariCP best practices

#### Example Projects
- [Spring Data Examples](https://github.com/spring-projects/spring-data-examples) - Database patterns
- [Cache Implementation Patterns](https://github.com/spring-projects/spring-boot/tree/main/spring-boot-project/spring-boot-autoconfigure/src/main/java/org/springframework/boot/autoconfigure/cache) - Spring caching

### Week 5-6: Advanced Data Management
#### Official Documentation
- [Spring Data JPA](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/) - Database operations
- [Hibernate Performance Guide](https://docs.jboss.org/hibernate/orm/current/performance/html_single/Hibernate_Performance_Guide.html) - Query optimization
- [Redis Enterprise](https://redis.com/redis-enterprise/technology/redis-enterprise-documentation/) - Advanced caching

#### Tutorials and Guides
- [Database Indexing Strategies](https://use-the-index-luke.com/) - Deep dive into indexing
- [Polyglot Persistence](https://martinfowler.com/bliki/PolyglotPersistence.html) - Multi-database architecture
- [Connection Pooling](https://github.com/brettwooldridge/HikariCP) - HikariCP best practices

#### Example Projects
- [Spring Data Examples](https://github.com/spring-projects/spring-data-examples) - Database patterns
- [Cache Implementation Patterns](https://github.com/spring-projects/spring-boot/tree/main/spring-boot-project/spring-boot-autoconfigure/src/main/java/org/springframework/boot/autoconfigure/cache) - Spring caching

### Week 7-8: Search and Basic Event Handling
#### Official Documentation
- [Spring Data Elasticsearch](https://docs.spring.io/spring-data/elasticsearch/docs/current/reference/html/) - Search setup
- [Spring Events](https://docs.spring.io/spring-framework/reference/core/beans/context-functionality.html#context-functionality-events) - Event handling
- [RabbitMQ with Spring](https://docs.spring.io/spring-amqp/reference/html/) - Message queues

#### Tutorials and Guides
- [Elasticsearch Tutorial](https://www.elastic.co/guide/en/elasticsearch/client/java-api-client/current/index.html) - Search implementation
- [Spring Events Tutorial](https://www.baeldung.com/spring-events) - Event handling
- [RabbitMQ Tutorial](https://www.rabbitmq.com/getstarted.html) - Message queues

#### Example Projects
- [Spring Data Elasticsearch Example](https://github.com/spring-projects/spring-data-examples/tree/main/elasticsearch) - Search implementation
- [Spring AMQP Examples](https://github.com/spring-projects/spring-amqp-samples) - Message handling

## Phase 2: Enhancing the Monolith (Weeks 9-14)

### Week 9-10: Domain Events and CQRS
#### Official Documentation
- [Spring Framework Events](https://docs.spring.io/spring-framework/reference/core/beans/context-functionality.html#context-functionality-events) - Event system
- [Axon Framework](https://docs.axoniq.io/reference-guide/) - CQRS implementation
- [Spring Integration](https://docs.spring.io/spring-integration/reference/html/overview.html) - Enterprise integration

#### Tutorials and Guides
- [CQRS Pattern](https://microservices.io/patterns/data/cqrs.html) - Martin Fowler's guide
- [Event Sourcing](https://microservices.io/patterns/data/event-sourcing.html) - Implementation patterns
- [Domain Events](https://www.baeldung.com/spring-data-ddd) - DDD with Spring

#### Example Projects
- [CQRS Example](https://github.com/AxonFramework/AxonFramework) - Axon reference
- [Event Sourcing Sample](https://github.com/spring-projects/spring-integration-samples) - Integration patterns

### Week 11-12: Modern API Architecture
#### Official Documentation
- [Spring Cloud Gateway](https://docs.spring.io/spring-cloud-gateway/docs/current/reference/html/) - API Gateway
- [GraphQL Spring Boot](https://docs.spring.io/spring-graphql/docs/current/reference/html/) - GraphQL implementation
- [Spring Security OAuth2](https://docs.spring.io/spring-security/reference/servlet/oauth2/index.html) - Modern auth

#### Tutorials and Guides
- [API Gateway Patterns](https://microservices.io/patterns/apigateway.html) - Implementation patterns
- [GraphQL Best Practices](https://graphql.org/learn/best-practices/) - Schema design and optimization
- [Zero Trust Architecture](https://www.nist.gov/publications/zero-trust-architecture) - NIST guidelines

#### Example Projects
- [Spring Cloud Gateway Sample](https://github.com/spring-cloud-samples/spring-cloud-gateway-sample) - Gateway patterns
- [GraphQL Spring Example](https://github.com/spring-projects/spring-graphql/tree/main/samples) - GraphQL implementation

### Week 13-14: Service Layer Refactoring
#### Official Documentation
- [Spring Service Layer](https://docs.spring.io/spring-framework/reference/core/beans/classpath-scanning.html) - Service components
- [Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html) - Uncle Bob's guide
- [Hexagonal Architecture](https://netflixtechblog.com/ready-for-changes-with-hexagonal-architecture-b315ec967749) - Netflix's approach

#### Tutorials and Guides
- [Clean Architecture with Spring](https://www.baeldung.com/spring-boot-clean-architecture) - Implementation guide
- [Service Layer Patterns](https://martinfowler.com/eaaCatalog/serviceLayer.html) - Martin Fowler's patterns
- [Refactoring Guide](https://refactoring.guru/) - Refactoring patterns

#### Example Projects
- [Clean Architecture Example](https://github.com/mattia-battiston/clean-architecture-example) - Reference implementation
- [Hexagonal Architecture Sample](https://github.com/thombergs/buckpal) - Spring example

## Phase 3: Transition to Microservices (Weeks 15-20)

### Week 15-16: Service Discovery and Gateway
#### Official Documentation
- [Spring Cloud Netflix](https://docs.spring.io/spring-cloud-netflix/docs/current/reference/html/) - Netflix OSS
- [Spring Cloud Gateway](https://docs.spring.io/spring-cloud-gateway/docs/current/reference/html/) - API Gateway
- [Eureka](https://github.com/Netflix/eureka/wiki) - Service discovery

#### Tutorials and Guides
- [Service Discovery Tutorial](https://spring.io/guides/gs/service-registration-and-discovery/) - Spring guide
- [API Gateway Pattern](https://microservices.io/patterns/apigateway.html) - Implementation patterns
- [Load Balancing](https://spring.io/guides/gs/client-side-load-balancing/) - Client-side balancing

#### Example Projects
- [Spring Cloud Samples](https://github.com/spring-cloud-samples) - Reference implementations
- [Spring Cloud Gateway Sample](https://github.com/spring-cloud/spring-cloud-gateway/tree/main/spring-cloud-gateway-sample) - Gateway example

### Week 17-18: System Scalability and Performance
#### Official Documentation
- [Spring WebFlux](https://docs.spring.io/spring-framework/reference/web/webflux.html) - Reactive programming
- [Project Reactor](https://projectreactor.io/docs/core/release/reference/) - Reactive streams
- [Spring Cloud Kubernetes](https://docs.spring.io/spring-cloud-kubernetes/docs/current/reference/html/) - K8s integration

#### Tutorials and Guides
- [Reactive Patterns](https://www.reactivemanifesto.org/) - Reactive system design
- [Load Management](https://resilience4j.readme.io/) - Circuit breaking and bulkheads
- [Kubernetes Patterns](https://containerpatterns.io/) - Container orchestration

#### Example Projects
- [Spring WebFlux Example](https://github.com/spring-projects/spring-framework/tree/main/spring-webflux) - Reactive patterns
- [Resilience4j Demo](https://github.com/resilience4j/resilience4j-spring-boot2-demo) - Resilience patterns

### Week 19-20: Modern Observability
#### Official Documentation
- [Spring Boot Actuator](https://docs.spring.io/spring-boot/docs/current/reference/html/actuator.html) - Built-in monitoring
- [OpenTelemetry](https://opentelemetry.io/docs/) - Distributed tracing
- [Micrometer](https://micrometer.io/docs) - Metrics collection

#### Tutorials and Guides
- [SLO Implementation](https://sre.google/sre-book/service-level-objectives/) - Google's SRE guide
- [Distributed Tracing](https://opentelemetry.io/docs/instrumentation/java/) - OpenTelemetry for Java
- [Metrics Best Practices](https://prometheus.io/docs/practices/naming/) - Prometheus patterns

#### Example Projects
- [Spring Boot Admin](https://github.com/codecentric/spring-boot-admin) - Admin UI
- [OpenTelemetry Demo](https://github.com/open-telemetry/opentelemetry-demo) - Tracing example

## Additional Resources

### Books
- "Clean Architecture" by Robert C. Martin
- "Domain-Driven Design" by Eric Evans
- "Building Microservices" by Sam Newman
- "Site Reliability Engineering" by Google
- "Designing Data-Intensive Applications" by Martin Kleppmann

### Online Courses
- [Advanced Spring Boot](https://www.baeldung.com/learn-spring-course) - Deep dive into Spring
- [Reactive Programming](https://www.pluralsight.com/courses/reactive-programming-java-rxjava-2) - RxJava and Project Reactor
- [Kubernetes for Developers](https://www.udemy.com/course/kubernetes-for-developers/) - Container orchestration
- [Distributed Systems](https://www.coursera.org/specializations/cloud-computing) - Cloud Computing Specialization

### Community Resources
- [Spring Blog](https://spring.io/blog)
- [InfoQ](https://www.infoq.com/architecture-design/)
- [Martin Fowler's Blog](https://martinfowler.com/)
- [Thoughtworks Tech Radar](https://www.thoughtworks.com/radar)
