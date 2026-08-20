# 🛒 Capstone E-Commerce System

![Build Status](https://img.shields.io/badge/build-passing-brightgreen)
![Architecture](https://img.shields.io/badge/architecture-microservices-blue)
![Deployment](https://img.shields.io/badge/deployment-Docker%20%7C%20Kubernetes-informational)
![Frontend](https://img.shields.io/badge/frontend-React%20%7C%20TypeScript-61DAFB)
![Backend](https://img.shields.io/badge/backend-Java%20%7C%20Python%20%7C%20Node.js-orange)
![License](https://img.shields.io/badge/license-MIT-green)

A **cloud-native e-commerce platform** built using a microservices architecture to demonstrate modern backend development, distributed systems, containerization, and cloud-native engineering practices.

The application separates major business capabilities such as **user profiles, shopping carts, product catalog, and search** into independently deployable services.

---

## 📌 Table of Contents

* [Overview](#-overview)
* [Project Objectives](#-project-objectives)
* [System Architecture](#-system-architecture)
* [Microservices](#-microservices)
* [Technology Stack](#-technology-stack)
* [Key Features](#-key-features)
* [Project Structure](#-project-structure)
* [Local Setup](#-local-setup)
* [API Documentation](#-api-documentation)
* [Engineering Highlights](#-engineering-highlights)
* [Docker & Kubernetes](#-docker--kubernetes)
* [Testing](#-testing)
* [Future Enhancements](#-future-enhancements)
* [Author](#-author)

---

# 📖 Overview

Traditional e-commerce applications often begin as a single monolithic application. As the application grows, independently scaling and maintaining individual business components becomes difficult.

This project explores a **microservices-based architecture** where each major business capability is isolated into its own service.

### Main Components

```text
                    ┌──────────────────────┐
                    │      React UI        │
                    │   TypeScript + MUI   │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   API / Nginx Proxy  │
                    └──────────┬───────────┘
                               │
          ┌────────────────────┼────────────────────┐
          │                    │                    │
          ▼                    ▼                    ▼
   ┌─────────────┐      ┌─────────────┐      ┌─────────────┐
   │ User Service│      │ Cart Service│      │Product      │
   │   FastAPI   │      │ Spring Boot │      │Service      │
   │   Python    │      │    Java     │      │ Express.js  │
   └──────┬──────┘      └──────┬──────┘      └──────┬──────┘
          │                    │                    │
          ▼                    ▼                    ▼
      SQLite                Redis                MongoDB

                               │
                               ▼
                       ┌────────────────┐
                       │ Search Service │
                       │    Node.js     │
                       └───────┬────────┘
                               │
                               ▼
                         Elasticsearch
```

---

# 🎯 Project Objectives

The project was developed to demonstrate practical understanding of:

* Object-oriented programming
* REST API development
* Microservices architecture
* Distributed application design
* Database-per-service architecture
* Containerization with Docker
* Kubernetes-based deployment
* Cloud-native development
* Asynchronous backend processing
* Caching with Redis
* Infrastructure as Code
* CI/CD practices

The primary objective is to understand **how independently developed services communicate, store data, and scale within a distributed application**.

---

# 🏗 System Architecture

The application follows a **loosely coupled microservices architecture**.

Each service:

* Owns a specific business responsibility
* Maintains its own dependencies
* Can be developed independently
* Can be containerized independently
* Can be deployed independently
* Uses a suitable persistence layer

### High-Level Flow

```text
User
 │
 ▼
React Storefront
 │
 ▼
Nginx / API Proxy
 │
 ├──────────────► User Profile Service
 │                       │
 │                       ▼
 │                    SQLite
 │
 ├──────────────► Shopping Cart Service
 │                       │
 │                       ▼
 │                     Redis
 │
 ├──────────────► Product Catalog Service
 │                       │
 │                       ▼
 │                    MongoDB
 │
 └──────────────► Search Service
                         │
                         ▼
                    Elasticsearch
```

---

# 🔧 Microservices

## 1. User Profile Service

**Technology:** Python + FastAPI

### Responsibilities

* User registration
* User retrieval
* User profile updates
* User data management

### Database

SQLite with asynchronous SQLAlchemy.

### Key Implementation

* Async API endpoints
* Async database access
* Dependency injection
* Data Access Layer
* Automatic API documentation

---

## 2. Shopping Cart Service

**Technology:** Java + Spring Boot

### Responsibilities

* Create shopping carts
* Add products
* Remove products
* Update quantities
* Retrieve active carts

### Database / Cache

Redis is used for fast access to temporary cart state.

### Key Concepts

* Java OOP
* Spring Boot
* REST APIs
* Dependency Injection
* Redis caching

---

## 3. Product Catalog Service

**Technology:** Node.js + Express.js

### Responsibilities

* Product creation
* Product retrieval
* Product updates
* Product categorization

### Database

MongoDB.

### Key Concepts

* REST API development
* JavaScript
* Node.js
* Express.js
* Document-oriented database

---

## 4. Search Service

**Technology:** Node.js

### Responsibilities

* Product search
* Keyword-based search
* Search indexing
* Search result retrieval

### Search Engine

Elasticsearch.

This service is separated from the main product database to allow search functionality to evolve independently.

---

# 💻 Technology Stack

| Layer             | Technology                     |
| ----------------- | ------------------------------ |
| Frontend          | React, TypeScript, Material UI |
| User Service      | Python, FastAPI                |
| Cart Service      | Java, Spring Boot              |
| Product Service   | Node.js, Express.js            |
| Search Service    | Node.js, Elasticsearch         |
| Databases         | SQLite, MongoDB                |
| Cache             | Redis                          |
| Containerization  | Docker, Docker Compose         |
| Orchestration     | Kubernetes                     |
| Infrastructure    | Terraform                      |
| Web Server        | Nginx                          |
| API Documentation | Swagger / OpenAPI              |
| Version Control   | Git / GitHub                   |

---

# ✨ Key Features

### 👤 User Management

* Create user profiles
* Retrieve user information
* Update profile information
* REST-based API

### 🛍 Product Management

* Product catalog
* Product retrieval
* Product categorization
* MongoDB persistence

### 🛒 Shopping Cart

* Add products
* Remove products
* Update quantities
* Redis-based cart storage

### 🔎 Product Search

* Keyword search
* Dedicated search service
* Elasticsearch indexing

### 🌐 Web Application

* React-based storefront
* TypeScript
* Material UI
* Nginx-based production serving

### 🐳 Containerization

Each service can be packaged as an independent Docker container.

### ☸️ Kubernetes

Services can be deployed using Kubernetes workloads and services.

---

# 📂 Project Structure

```text
capstone-ecommerce/
│
├── store-ui/
│   ├── src/
│   ├── public/
│   ├── package.json
│   └── Dockerfile
│
├── users-cna-microservice/
│   ├── app/
│   ├── tests/
│   ├── requirements.txt
│   ├── Dockerfile
│   └── app.py
│
├── cart-cna-microservice/
│   ├── src/
│   ├── build.gradle
│   ├── Dockerfile
│   └── README.md
│
├── products-cna-microservice/
│   ├── src/
│   ├── package.json
│   ├── Dockerfile
│   └── README.md
│
├── search-cna-microservice/
│   ├── src/
│   ├── package.json
│   ├── Dockerfile
│   └── README.md
│
├── infra/
│   ├── docker/
│   ├── kubernetes/
│   └── terraform/
│
├── docker-compose.yml
├── README.md
└── .gitignore
```

---

# ⚙️ Prerequisites

Install the following before running the project:

* Docker
* Docker Compose
* Node.js 18+
* npm
* Python 3.10+
* pip / pipenv
* Java JDK 11+
* Gradle
* Git

For Kubernetes deployment:

* Kubernetes
* kubectl
* Minikube or Docker Desktop Kubernetes

---

# 🚀 Local Setup

## Step 1 — Clone the Repository

```bash
git clone https://github.com/yourusername/capstone-ecommerce.git

cd capstone-ecommerce
```

---

## Step 2 — Start Infrastructure

Start the required databases and supporting services:

```bash
docker compose up -d
```

Check running containers:

```bash
docker ps
```

---

# 🐍 Step 3 — Start User Service

Navigate to the User Service:

```bash
cd users-cna-microservice
```

Install dependencies:

```bash
pipenv install
```

Activate the environment:

```bash
pipenv shell
```

Start the application:

```bash
python app.py
```

The API will be available at:

```text
http://127.0.0.1:9090
```

Swagger documentation:

```text
http://127.0.0.1:9090/docs
```

---

# ⚛️ Step 4 — Start React Frontend

Open another terminal:

```bash
cd store-ui
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm start
```

Frontend:

```text
http://localhost:3000
```

---

# 📡 API Documentation

The User Profile Service provides automatically generated Swagger/OpenAPI documentation.

Open:

```text
http://127.0.0.1:9090/docs
```

## User APIs

| Method | Endpoint           | Description              |
| ------ | ------------------ | ------------------------ |
| GET    | `/users`           | Retrieve all users       |
| GET    | `/users/{user_id}` | Retrieve a specific user |
| POST   | `/users`           | Create a new user        |
| PUT    | `/users/{user_id}` | Update user information  |

### Example Request

```http
POST /users
Content-Type: application/json
```

```json
{
  "name": "Rahul Kumar",
  "email": "rahul@example.com",
  "mobile": "9876543210"
}
```

---

# 🧠 Engineering Highlights

## 1. Asynchronous Database Access

The User Profile Service uses asynchronous database operations with:

* `aiosqlite`
* Async SQLAlchemy
* FastAPI async endpoints

This prevents unnecessary blocking during database I/O.

---

## 2. Dependency Injection

FastAPI dependency injection is used to separate:

```text
API Layer
    ↓
Business Logic
    ↓
Data Access Layer
    ↓
Database
```

This improves:

* Maintainability
* Testability
* Separation of concerns

---

## 3. Database-per-Service Design

Each service is responsible for its own persistence layer.

```text
User Service       → SQLite
Cart Service       → Redis
Product Service    → MongoDB
Search Service     → Elasticsearch
```

This reduces tight coupling between services.

---

## 4. Redis for Cart State

Shopping cart information is stored in Redis because cart operations require:

* Low latency
* Frequent reads/writes
* Temporary state management

This avoids unnecessary database queries for frequently accessed cart information.

---

## 5. Containerized Services

Each application component has its own Docker configuration.

Example:

```text
Frontend       → Docker Container
User API       → Docker Container
Cart API       → Docker Container
Product API    → Docker Container
Search API     → Docker Container
```

This provides consistent development and deployment environments.

---

## 6. Multi-Stage Frontend Build

The React application uses a multi-stage Docker build.

```text
Node.js
   ↓
Build React Application
   ↓
Static Files
   ↓
Nginx
```

This keeps the production container lightweight and separates the build environment from the runtime environment.

---

# 🐳 Docker & Kubernetes

## Docker

Build a service:

```bash
docker build -t user-service .
```

Run the container:

```bash
docker run -p 9090:9090 user-service
```

View running containers:

```bash
docker ps
```

---

## Kubernetes

Example deployment flow:

```bash
kubectl apply -f infra/kubernetes/
```

Check pods:

```bash
kubectl get pods
```

Check services:

```bash
kubectl get services
```

View logs:

```bash
kubectl logs <pod-name>
```

Scale a service:

```bash
kubectl scale deployment cart-service --replicas=3
```

The Kubernetes deployment demonstrates:

* Container orchestration
* Service discovery
* Replica management
* Horizontal scaling
* Declarative deployment

---

# 🧪 Testing

Testing is organized at the service level.

Planned / implemented tests include:

### Backend

* Unit tests
* API tests
* Integration tests

### Frontend

* Component tests
* API integration tests

### Example

```text
tests/
├── unit/
├── integration/
└── api/
```

---

# 🔄 CI/CD

The project can be integrated with GitHub Actions to automate:

```text
Git Push
   ↓
Build
   ↓
Run Tests
   ↓
Build Docker Images
   ↓
Push Images
   ↓
Deploy
```

Example workflow:

```text
.github/
└── workflows/
    └── ci-cd.yml
```

---

# 🔐 Security Considerations

Future production hardening includes:

* JWT-based authentication
* Role-based authorization
* Environment-based secrets
* API rate limiting
* HTTPS
* Kubernetes Secrets
* AWS IAM least-privilege policies

Secrets should never be committed directly to the repository.

---

# 📈 Future Enhancements

The following improvements can extend the platform:

### Infrastructure

* AWS deployment
* Terraform-based infrastructure
* Kubernetes Ingress
* Horizontal Pod Autoscaler

### Distributed Systems

* RabbitMQ / Kafka
* Event-driven communication
* Retry mechanisms
* Circuit breakers

### Security

* OAuth2 / JWT authentication
* Role-based access control
* API Gateway

### Observability

* Prometheus
* Grafana
* Centralized logging
* Distributed tracing

### Testing

* PyTest
* JUnit
* Jest
* Integration testing
* End-to-end testing

---

# 🎓 What This Project Demonstrates

This project demonstrates practical understanding of:

```text
Java & OOP
     ↓
Spring Boot
     ↓
REST APIs
     ↓
Microservices
     ↓
Docker
     ↓
Kubernetes
     ↓
Cloud-Native Architecture
     ↓
CI/CD
```

Along with experience in:

* Python / FastAPI
* React / TypeScript
* Node.js
* Redis
* MongoDB
* Elasticsearch
* Docker
* Kubernetes
* Terraform
* Distributed systems

---

# 👨‍💻 Author

**Rahul Kumar**

B.Tech- National Institute of Technology, Calicut

### Connect

* GitHub: `https://github.com/upsehu`
* LinkedIn: `https://www.linkedin.com/in/rahul-kumar-9b0798281/`

---

## ⭐ Project Status

**Status:** Active Development

This project is being developed as a **college-level cloud-native engineering project** with emphasis on practical backend development, containerization, distributed systems, and DevOps.

If you find the project useful, consider giving the repository a ⭐.

