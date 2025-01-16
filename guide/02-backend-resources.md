# Backend Learning Resources
Aligned with evolutionary approach from monolith to microservices and senior development practices

## Phase 1: Monolithic Foundation (Weeks 1-8)

### Week 1-2: Project Setup and Modern Development Practices

- [Spring Boot Reference](https://docs.spring.io/spring-boot/reference/using/index.html) - Core concepts and setup
- [Git Basics](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository) - Git Basics
- [Git Branching - Branches in a Nutshell](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell) - Git Branching - Branches in a Nutshell

- [Code Review Best Practices](https://google.github.io/eng-practices/review/) - Google's Engineering Practices
- [Technical Debt Assessment](https://martinfowler.com/bliki/TechnicalDebt.html) - Understanding and managing debt


### Week 3-6: Core Models and Advanced Data Management

- [Spring Data JPA](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/) - Database operations
- [Hibernate Performance Guide](https://www.adservio.fr/post/hibernate-performance-best-practices#:~:text=Hibernate%20performance%20best%20practices%20include,logging%20SQL%20statements%2C%20and%20else.&text=Performance%20tuning%20is%20important%20for,for%20data%2Ddriven%20web%20applications.) - Query optimization
- [Caching](https://medium.com/@abhirup.acharya009/caching-system-design-fundamentals-226795bd9072#:~:text=Caches%20come%20in%20various%20levels,to%20cost%20and%20physical%20limitations.) - Caching

- [Deep dive into indexing](https://medium.com/picus-security-engineering/deep-dive-into-sql-indexes-cef384042e86) - Deep dive into indexing
- [Polyglot Persistence](https://martinfowler.com/bliki/PolyglotPersistence.html) - Multi-database architecture
- [Connection Pooling](https://github.com/brettwooldridge/HikariCP) - HikariCP best practices



### Week 7-8: Search and Basic Event Handling

- [Spring Data Elasticsearch](https://docs.spring.io/spring-data/elasticsearch/docs/current/reference/html/) - Search setup
- [Spring Events](https://docs.spring.io/spring-modulith/reference/events.html) - Event handling
- [RabbitMQ with Spring](https://docs.spring.io/spring-amqp/reference/introduction/quick-tour.html) - Message queues


- [Elasticsearch Tutorial](https://www.elastic.co/guide/en/elasticsearch/client/java-api-client/current/index.html) - Search implementation
- [Spring Events Tutorial](https://www.baeldung.com/spring-events) - Event handling
- [Spring AMQP](https://www.rabbitmq.com/getstarted.html) - Message queues


## Phase 2: Enhancing the Monolith (Weeks 9-14)

### Week 9-10: Domain Events and CQRS

- [Axon Framework](https://docs.axoniq.io/reference-guide/) - CQRS implementation
- [CQRS Pattern](https://microservices.io/patterns/data/cqrs.html) - Martin Fowler's guide
- [Event Sourcing](https://microservices.io/patterns/data/event-sourcing.html) - Implementation patterns
- [Domain Events](https://www.baeldung.com/spring-data-ddd) - DDD with Spring


### Week 11-12: Modern API Architecture

- [Spring Cloud Gateway](https://docs.spring.io/spring-cloud-gateway/docs/current/reference/html/) - API Gateway
- [GraphQL Spring Boot](https://docs.spring.io/spring-graphql/docs/current/reference/html/) - GraphQL implementation
- [Spring Security OAuth2](https://docs.spring.io/spring-security/reference/servlet/oauth2/index.html) - Modern auth
- [API Gateway Patterns](https://microservices.io/patterns/apigateway.html) - Implementation patterns
- [GraphQL Best Practices](https://graphql.org/learn/best-practices/) - Schema design and optimization

### Week 13-14: Service Layer Refactoring

- [Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html) - Uncle Bob's guide
- [Hexagonal Architecture](https://netflixtechblog.com/ready-for-changes-with-hexagonal-architecture-b315ec967749) - Netflix's approach


- [Clean Architecture with Spring](https://www.baeldung.com/spring-boot-clean-architecture) - Implementation guide
- [Service Layer Patterns](https://martinfowler.com/eaaCatalog/serviceLayer.html) - Martin Fowler's patterns
- [Refactoring Guide](https://refactoring.guru/refactoring) - Refactoring patterns


## Phase 3: Transition to Microservices (Weeks 15-20)

### Week 15-16: Service Discovery and Gateway

- [Spring Cloud Netflix](https://docs.spring.io/spring-cloud-netflix/docs/current/reference/html/) - Netflix OSS
- [API Gateway Pattern](https://microservices.io/patterns/apigateway.html) - Implementation patterns
- [Spring Cloud Gateway](https://docs.spring.io/spring-cloud-gateway/docs/current/reference/html/) - API Gateway
- [Eureka](https://github.com/Netflix/eureka/wiki) - Service discovery
- [Service Discovery Tutorial](https://spring.io/guides/gs/service-registration-and-discovery/) - Spring guide
- [Load Balancing](https://spring.io/guides/gs/client-side-load-balancing/) - Client-side balancing


### Week 17-18: System Scalability and Performance

- [Spring WebFlux](https://docs.spring.io/spring-framework/reference/web/webflux.html) - Reactive programming
- [Project Reactor](https://projectreactor.io/docs/core/release/reference/) - Reactive streams
- [Spring Cloud Kubernetes](https://docs.spring.io/spring-cloud-kubernetes/docs/current/reference/html/) - K8s integration


- [Reactive Patterns](https://www.reactivemanifesto.org/) - Reactive system design
- [Load Management](https://resilience4j.readme.io/docs/circuitbreaker) - Circuit breaking and bulkheads


### Week 19-20: Modern Observability

- [Spring Boot Actuator](https://docs.spring.io/spring-boot/docs/current/reference/html/actuator.html) - Built-in monitoring
- [OpenTelemetry](https://opentelemetry.io/docs/) - Distributed tracing
- [Micrometer](https://micrometer.io/docs) - Metrics collection


- [SLO Implementation](https://sre.google/sre-book/service-level-objectives/) - Google's SRE guide
- [Distributed Tracing](https://opentelemetry.io/docs/instrumentation/java/) - OpenTelemetry for Java
- [Metrics Best Practices](https://prometheus.io/docs/practices/naming/) - Prometheus patterns


## Additional Resources

### Books
- "Clean Architecture" by Robert C. Martin
- "Domain-Driven Design" by Eric Evans
- "Building Microservices" by Sam Newman
- "Site Reliability Engineering" by Google
- "Designing Data-Intensive Applications" by Martin Kleppmann

### Online Courses
- [Distributed Systems](https://www.coursera.org/specializations/cloud-computing) - Cloud Computing Specialization
