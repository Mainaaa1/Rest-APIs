# Week 9 – REST APIs

## Day 5: Swagger Documentation (13 Mar 2026)

### Overview

Today I explored **API documentation using Swagger (OpenAPI Specification)**. Proper documentation is essential for making APIs understandable, testable, and easy to integrate with.

Swagger provides a standardized way to describe API endpoints, request/response formats, authentication methods, and more.

---

### What is Swagger / OpenAPI?

The **OpenAPI Specification (OAS)** is a standard for describing REST APIs.

Swagger is a set of tools built around this specification that helps developers:

* Document APIs
* Visualize endpoints
* Test API calls directly from the browser

---

### Key Components of OpenAPI

An OpenAPI document typically includes:

* API metadata (title, version, description)
* Paths (endpoints)
* Request parameters
* Response formats
* Authentication methods

Example snippet:

```yaml
openapi: 3.0.0
info:
  title: User API
  version: 1.0.0
paths:
  /users:
    get:
      summary: Get all users
      responses:
        200:
          description: Successful response
```

---

### Swagger UI

Swagger UI provides an interactive interface where developers can:

* View all available endpoints
* Expand endpoint details
* Send live API requests
* Inspect responses in real time

This significantly improves the developer experience.

---

### Benefits of API Documentation

Well-documented APIs provide:

* Faster onboarding for developers
* Reduced miscommunication between teams
* Easier debugging and testing
* Better maintainability

---

### Integrating Swagger in Applications

Common approaches:

* Using libraries (e.g., Swagger UI Express, NestJS Swagger module)
* Auto-generating docs from code annotations
* Maintaining a separate OpenAPI YAML/JSON file

---

### Best Practices

Key lessons learned:

* Keep documentation up to date with code changes
* Use clear and concise endpoint descriptions
* Include example requests and responses
* Document error responses
* Version your API documentation alongside your API

---

### Reflection

Documentation is often overlooked but is critical for API adoption. Swagger simplifies the process by providing both a standard specification and interactive tools. Well-documented APIs are easier to use, maintain, and scale.
