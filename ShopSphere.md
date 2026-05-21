# ShopSphere - Production Ready Multi-Vendor E-Commerce Marketplace

## Project Vision

Build a production-ready, microservices-based e-commerce platform using:

* Spring Boot
* Spring Security
* JWT Authentication & Authorization
* Spring Cloud Gateway
* Eureka Service Discovery
* MySQL
* Angular
* Kafka
* Redis
* Docker
* Kubernetes
* Prometheus
* Grafana

---

# Development Philosophy

The biggest reason projects fail is not coding difficulty.

It is:

* Lack of planning
* Inconsistency
* Rushing into coding
* Changing architecture midway

We will follow this rule throughout the project:

```text
Design First
    ↓
Implement Second
    ↓
Refactor Third
    ↓
Deploy Last
```

Never:

```text
Code First
    ↓
Fix Later
```

---

# Business Domain

## ShopSphere

A Multi-Vendor E-Commerce Marketplace

---

# User Roles

## ADMIN

Responsibilities:

* Manage users
* Manage sellers
* Manage products
* Monitor orders
* View analytics dashboard
* Block or activate users
* Manage categories

---

## SELLER

Responsibilities:

* Add products
* Update products
* Delete products
* Manage inventory
* View orders
* View sales and revenue

---

## CUSTOMER

Responsibilities:

* Register
* Login
* Browse products
* Search products
* Filter products
* Add products to cart
* Remove products from cart
* Place orders
* Track orders
* Manage profile
* Manage addresses
* Wishlist products

---

# Final Architecture

```text
                     Angular Frontend
                             │
                             ▼
                       API Gateway
                             │
      ┌──────────────────────┼──────────────────────┐
      │                      │                      │
      ▼                      ▼                      ▼
 Auth Service         Product Service        User Service
      │                      │                      │
      ▼                      ▼                      ▼
  auth_db              product_db             user_db

      ┌──────────────────────┼──────────────────────┐
      │                      │
      ▼                      ▼
 Cart Service          Order Service
      │                      │
      ▼                      ▼
  cart_db              order_db

                             │
                             ▼
                 Notification Service
```

Future Enhancements:

```text
Kafka
Redis
Docker
Kubernetes
Monitoring
Logging
CI/CD
```

---

# Core Microservice Principles

## Rule #1 - Database Per Service

Never:

```text
Auth Service
Product Service
Cart Service

       ↓

Same Database
```

Always:

```text
auth_db
product_db
cart_db
order_db
user_db
```

Each service owns its own data.

---

## Rule #2 - Never Trust Frontend

Example:

Frontend sends:

```json
{
  "price": 10
}
```

Backend must validate everything.

Business rules always belong to Spring Boot services.

Never trust Angular input.

---

## Rule #3 - DTOs Everywhere

Avoid:

```java
@PostMapping
public Product save(@RequestBody Product product)
```

Use:

```java
ProductRequest
ProductResponse
```

Benefits:

* Better API design
* Better validation
* Better maintainability
* Safer future refactoring

---

## Rule #4 - Layered Architecture

Every microservice must follow:

```text
controller
service
repository
entity
dto
mapper
exception
config
security
```

No shortcuts.

---

# Security Standards

The following are mandatory:

## Authentication

* JWT Authentication
* BCrypt Password Encoding

## Authorization

* Role-Based Access Control (RBAC)

Roles:

```text
ROLE_ADMIN
ROLE_SELLER
ROLE_CUSTOMER
```

## Security Architecture

```text
Client
   ↓
API Gateway
   ↓
JWT Validation
   ↓
Microservices
```

---

# Clean Code Standards

Mandatory practices:

* Constructor Injection
* DTO Pattern
* Global Exception Handling
* Validation Annotations
* Service Layer Separation
* Repository Layer Separation
* SOLID Principles
* Meaningful Naming Conventions

---

# Angular Standards

Frontend must use:

## Forms

* Reactive Forms

## Routing

* Route Guards

## Authentication

* JWT Interceptor

## Architecture

```text
components
services
models
guards
interceptors
shared
```

---

# Three-Day Execution Plan

---

# Day 1

## Infrastructure

Completed:

* Eureka Server
* API Gateway
* Auth Service
* Spring Security
* JWT Authentication
* JWT Authorization
* Gateway Integration

---

## Product Service

Modules:

* Product
* Category
* Inventory

Features:

```http
POST   /products
GET    /products
GET    /products/{id}
PUT    /products/{id}
DELETE /products/{id}

GET    /products/search
GET    /products/category/{id}
```

Security:

* JWT Protected

---

## User Service

Modules:

* Profile
* Address

Features:

```http
GET /users/profile
PUT /users/profile

POST /users/address
GET  /users/address
PUT  /users/address/{id}
DELETE /users/address/{id}
```

---

# Day 2

## Cart Service

Features:

```text
Add Item
Remove Item
Update Quantity
Get Cart
Clear Cart
```

Endpoints:

```http
POST   /cart/items
GET    /cart
PUT    /cart/items/{id}
DELETE /cart/items/{id}
```

---

## Order Service

Features:

```text
Place Order
Order History
Order Details
Cancel Order
Track Order
```

Order Lifecycle:

```text
CREATED
PAID
SHIPPED
DELIVERED
CANCELLED
```

Endpoints:

```http
POST /orders
GET  /orders
GET  /orders/{id}
PUT  /orders/{id}/cancel
```

---

## Angular Frontend

Pages:

* Login
* Register
* Product Listing
* Product Details
* Cart
* Orders
* Profile

---

# Day 3

## Kafka Integration

Events:

```text
OrderCreatedEvent
OrderCancelledEvent
```

Consumer:

```text
Notification Service
```

Responsibilities:

* Email Notifications
* Order Notifications

---

## Redis Integration

Caching:

```text
Product List
Popular Products
Frequently Accessed Products
```

Benefits:

* Faster API Response
* Reduced Database Load

---

## Docker

Containerize:

```text
API Gateway
Auth Service
Product Service
User Service
Cart Service
Order Service
MySQL
```

---

## Kubernetes

Deploy:

```text
Deployments
Services
ConfigMaps
Secrets
Ingress
```

---

## Monitoring & Logging

Tools:

```text
Spring Boot Actuator
Prometheus
Grafana
```

Monitoring:

* Health Checks
* JVM Metrics
* Request Metrics
* Service Monitoring

---

# Product Service Design

## Product Entity

Fields:

```text
id
name
description
price
stockQuantity
brand
category
imageUrl
sellerId
createdAt
updatedAt
status
```

---

## Category Entity

Fields:

```text
id
name
description
```

---

## Product Status

```text
ACTIVE
OUT_OF_STOCK
DISCONTINUED
```

---

## Product APIs

```http
POST   /products

GET    /products

GET    /products/{id}

PUT    /products/{id}

DELETE /products/{id}

GET    /products/search

GET    /products/category/{id}
```

---

# Current Progress

Completed:

* Eureka Server
* API Gateway
* Auth Service
* JWT Authentication
* JWT Authorization
* Global Exception Handling
* BCrypt Password Encoding
* Gateway JWT Validation
* Service Discovery Integration

Next Task:

```text
Product Service Implementation
```

Goal:

Build a production-ready microservices e-commerce platform that demonstrates:

* Enterprise Spring Boot Development
* Angular Development
* Microservice Architecture
* Security Best Practices
* Distributed Systems Concepts
* Cloud-Native Deployment

```
```
