# Expense Tracker API

A RESTful API for managing personal expenses, built with **Python and FastAPI**.

The project is designed to demonstrate practical backend development fundamentals, including REST API design, relational database modelling, automated testing, TDD-oriented development, containerization, and maintainable application architecture.

> **Project status: In development**

---

## Overview

Expense Tracker API is a backend application for managing personal financial expenses through a REST API.

The project was created as the first practical backend project in a structured learning roadmap, with the goal of consolidating the fundamentals required to build maintainable Python backend applications.

The focus is on **backend engineering fundamentals rather than feature quantity**, with particular attention to API design, data persistence, validation, automated testing, and code organization.

---

## Planned & Implemented Features

The application is being developed progressively.

### Expense Management

* Create expenses
* Retrieve expenses
* Update expenses
* Delete expenses
* Expense categorization
* Expense amounts
* Expense dates
* Expense descriptions

### API

* RESTful API design
* Request validation
* Response serialization
* HTTP status codes
* Error handling
* OpenAPI documentation
* Swagger UI

### Database

* PostgreSQL
* Relational data modelling
* SQLAlchemy ORM
* Alembic database migrations

### Testing

* Unit testing
* Integration testing
* API testing
* pytest
* HTTPX
* TDD-oriented development

### Development Environment

* Docker
* Docker Compose
* Environment-based configuration

---

## Technology Stack

### Backend

* Python
* FastAPI
* Pydantic

### Database

* PostgreSQL
* SQLAlchemy
* Alembic

### Testing

* pytest
* HTTPX
* pytest-asyncio
* Unit testing
* Integration testing

### Development & DevOps

* Git
* GitHub
* Docker
* Docker Compose
* Linux
* CI/CD

---

## Architecture

The application follows a layered architecture designed to separate API concerns, business logic, and data access.

The high-level structure is:

```text
Client
   │
   ▼
FastAPI
   │
   ├── API / Routes
   │
   ├── Schemas
   │
   ├── Business Logic
   │
   └── Data Access
           │
           ▼
       PostgreSQL
```

The project also uses **Dependency Injection** to manage application dependencies and improve testability and maintainability.

The architecture may evolve as additional requirements are identified during development.

---

## Database

PostgreSQL is used as the primary relational database.

SQLAlchemy provides the ORM layer, while Alembic is used to manage database schema migrations.

The project focuses on maintaining a clear separation between application models, database persistence, and API schemas.

---

## Testing Strategy

Testing is a core part of the project.

The testing strategy includes:

### Unit Tests

Testing individual components and pieces of business logic in isolation.

### Integration Tests

Testing interactions between application components and the database.

### API Tests

Testing HTTP endpoints, request validation, response data, and error conditions.

### TDD-Oriented Development

The project follows a TDD-oriented workflow where appropriate:

```text
Write Test
    ↓
Implement
    ↓
Run Tests
    ↓
Refactor
    ↓
Repeat
```

The objective is not simply to achieve test coverage, but to use tests to improve software design and confidence in the application.

---

## Docker

Docker is used to provide a reproducible development environment.

The application and database can be run through Docker Compose, allowing the development environment to be recreated consistently.

A simplified environment looks like:

```text
┌─────────────────┐
│   FastAPI API   │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│   PostgreSQL    │
└─────────────────┘
```

---

## API Documentation

FastAPI automatically generates OpenAPI documentation for the API.

Interactive API documentation is provided through Swagger UI.

The documentation will evolve together with the API as new endpoints are implemented.

---

## Development Roadmap

### Phase 1 — Project Setup

* [x] Repository setup
* [ ] FastAPI application structure
* [ ] Configuration management
* [ ] Docker development environment
* [ ] PostgreSQL integration

### Phase 2 — Database

* [ ] SQLAlchemy models
* [ ] Database relationships
* [ ] Alembic configuration
* [ ] Initial migrations

### Phase 3 — Expense API

* [ ] Create expenses
* [ ] Retrieve expenses
* [ ] Update expenses
* [ ] Delete expenses
* [ ] Request validation
* [ ] Error handling
* [ ] API documentation

### Phase 4 — Testing

* [ ] Test infrastructure
* [ ] Unit tests
* [ ] Integration tests
* [ ] API tests
* [ ] TDD workflow
* [ ] Edge-case testing

### Phase 5 — Code Quality & CI/CD

* [ ] Code quality checks
* [ ] Automated test execution
* [ ] CI pipeline
* [ ] Improve application documentation
* [ ] Review architecture

---

## Project Goals

The main objectives of this project are to gain practical experience with:

* Building REST APIs with FastAPI
* Designing relational databases
* Using SQLAlchemy effectively
* Managing database migrations with Alembic
* Writing automated tests with pytest
* Applying TDD-oriented development
* Working with Docker
* Structuring maintainable backend applications
* Applying dependency injection
* Documenting APIs with OpenAPI
* Using Git and GitHub as part of the development workflow

---

## Project Status

**Current status: In development**

This project is the first backend project in a progressive learning roadmap.

Its purpose is to establish a strong foundation in Python backend development before moving on to a larger production-oriented SaaS application.

---

## Author

**Daniel López Berrocal**

Python · FastAPI · REST APIs · PostgreSQL · SQLAlchemy · Testing · Docker
