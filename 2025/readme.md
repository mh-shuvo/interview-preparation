# Programming & Software Engineering Concepts
## Clean Code & SonarQube
* Writing readable, maintainable, and scalable code.
* SonarQube: Static code analysis tool for detecting vulnerabilities, bugs, and code smells in PHP.
* Key clean code principles: meaningful variable names, single responsibility, avoiding deep nesting, and proper documentation.
* Linting for PHP & Laravel
* Tools like PHP_CodeSniffer and PHPStan for code linting.
* Laravel-specific linters: Laravel Pint, PHP Insights.
* Benefits: Code consistency, fewer runtime errors.

## SOLID Principles
* S: Single Responsibility
* O: Open/Closed Principle
* L: Liskov Substitution
* I: Interface Segregation
* D: Dependency Inversion
## How Laravel follows SOLID (e.g., Service Providers, Repositories).
## Service Provider & Service Container
* Service Provider: Registers dependencies and bootstraps services in Laravel.
* Service Container (IoC Container): Resolves class dependencies automatically (Dependency Injection).
* Example of binding and resolving services.
## Request-Response Lifecycle in PHP & Laravel
* PHP lifecycle from request initiation to response generation.
## Laravel’s lifecycle:
* Entry through public/index.php
* Kernel handling (app/Http/Kernel.php)
* Middleware execution
* Controller execution
* Response returned.
## Database & Optimization
* Database Indexing
Types: Primary Index, Unique Index, Composite Index, Full-text Index.
Pros and cons of indexing.
When not to use an index.

## Database Trigger, Function, Procedures
* Triggers: Automatic actions on INSERT, UPDATE, DELETE.
* Stored Procedures: Precompiled SQL stored in DB.
* Functions: Reusable SQL logic returning a value.
* Query Builder vs ORM vs Raw Query in Laravel
* Eloquent ORM: Object-based querying.
* Query Builder: Fluent query API, more optimized.
* Raw Queries: Direct SQL, best for complex queries.
## Caching & Message Queues
## Redis
* Caching queries and sessions using Redis.
* Difference between APCu, Memcached, and Redis.
* Laravel’s Redis integration (Predis vs phpredis).
## Message Brokers
## Kafka vs RabbitMQ:
* Kafka: High throughput, log-based, best for event-driven architecture.
* RabbitMQ: Lower latency, message queue, best for transactional processing.
* Use case in Laravel: Laravel Horizon with Redis queues.
## Software Engineering & DevOps
## Git Fetch vs Git Pull
** git fetch: Fetches changes without merging.
** git pull: Fetches and merges.
** When to use fetch over pull.
## How to Roll Back to a Specific Commit
** git reset --hard <commit-hash>
** git revert <commit-hash> (safe for shared branches).
## API Development & Security
### REST API
* RESTful principles: Stateless, Cacheable, Uniform Interface.
* Best practices for designing REST APIs.
* How to Secure and Version Your API
## Security:
* JWT authentication (Laravel Sanctum / Passport).
* Rate limiting (throttling).
CSRF & CORS protection.
* Input validation.
Versioning:
* URI versioning (/api/v1/users).
* Header-based versioning.
* Subdomain-based versioning.
* SQL Injection
* Preventing SQL injection in Laravel (Eloquent, Query Builder, Prepared Statements).
* Laravel’s QueryException handling.
## System Architecture & Scalability
* Monolith vs Microservice
* Monolith: Single application structure.
* Microservice: Independent, modular services communicating via APIs.
* Laravel in microservices (Lumen, API Gateway).
* How to Scale a Laravel Application to Serve Millions of Users & Handle Large Data
* Horizontal Scaling: Load balancing with Nginx.
* Vertical Scaling: Optimizing SQL queries, caching.
* Database Partitioning: Sharding, replication.
* Queue Optimization: Supervisor, Laravel Horizon.
* Throttling
* Rate limiting APIs using Laravel’s ThrottleRequests middleware.
* Preventing brute force attacks.
## Latest Features
### PHP 8+ Features:
* JIT Compiler
* Match Expressions
* Attributes
* Named Arguments
* Fibers (PHP 8.1)
* Readonly Properties (PHP 8.1)
* First-Class Callable Syntax (PHP 8.1)
* Deprecation of Dynamic Properties (PHP 8.2)
## Latest Laravel Features
* Native Pest Testing.
* Process Handling with Laravel Precognition.
* New Eloquent Model Defaults.
* Improved Job Batching.
* Additional Topics to Prepare
You’ve covered most major areas. A few more advanced topics that might come up:

* TDD (Test-Driven Development): Unit testing with PHPUnit, Laravel Dusk.
* CQRS & Event Sourcing: Separation of Read and Write models.
* Containerization: Running Laravel in Docker, using Kubernetes.
* GraphQL in Laravel: When to use GraphQL over REST.