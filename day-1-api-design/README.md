# Week 9 – REST APIs

## Day 1: API Design (9 Mar 2026)

### Overview

Today I focused on understanding the fundamentals of designing well-structured REST APIs. API design plays a critical role in how services communicate, how maintainable a system becomes over time, and how easily other developers can integrate with it.

The goal was to learn how to design APIs that are predictable, scalable, and easy to consume.

---

### What is a REST API?

A REST API (Representational State Transfer) is an architectural style used for building web services that communicate over HTTP. In RESTful systems, resources are identified by URLs and manipulated using standard HTTP methods.

Example:

```
GET /api/users
```

This endpoint retrieves a collection of users from the server.

---

### Core REST Principles

While studying REST APIs, I explored the main principles that guide RESTful design:

**1. Client–Server Separation**
The client handles the user interface while the server manages the data and logic.

**2. Stateless Communication**
Each request from the client must contain all information needed for the server to process it.

**3. Resource-Based Design**
APIs should expose resources rather than actions.

**4. Standard HTTP Methods**
Operations are performed using HTTP verbs such as GET, POST, PUT, and DELETE.

---

### Designing Resource-Based Endpoints

A key concept in REST API design is thinking in terms of **resources**.

Examples of resources:

* users
* products
* orders
* projects

A properly structured API might look like this:

```
GET /api/users
GET /api/users/{id}
POST /api/users
PUT /api/users/{id}
DELETE /api/users/{id}
```

This structure keeps endpoints intuitive and predictable.

---

### Proper Use of HTTP Methods

Each HTTP method has a specific purpose.

| Method | Purpose                     |
| ------ | --------------------------- |
| GET    | Retrieve data               |
| POST   | Create a new resource       |
| PUT    | Update an existing resource |
| PATCH  | Partially update a resource |
| DELETE | Remove a resource           |

Example request:

```
POST /api/users
```

Example response:

```json
{
  "id": 12,
  "name": "Jane Doe",
  "email": "jane@example.com"
}
```

---

### HTTP Status Codes

Using correct HTTP status codes helps API consumers understand what happened during a request.

Common status codes:

| Code | Meaning               |
| ---- | --------------------- |
| 200  | Successful request    |
| 201  | Resource created      |
| 400  | Bad request           |
| 401  | Unauthorized          |
| 404  | Resource not found    |
| 500  | Internal server error |

Example:

```
HTTP/1.1 201 Created
```

---

### Designing Consistent Responses

Consistency makes APIs easier to work with.

Example structured response:

```json
{
  "status": "success",
  "data": {
    "id": 1,
    "name": "John Doe"
  },
  "message": "User retrieved successfully"
}
```

Benefits of consistent responses:

* Easier frontend integration
* Better debugging
* Predictable API behavior

---

### Error Handling

APIs should return meaningful error messages.

Example error response:

```json
{
  "status": "error",
  "message": "User not found",
  "code": 404
}
```

Good error handling improves the developer experience when integrating with the API.

---

### Key Best Practices Learned

* Use nouns instead of verbs in endpoint names
* Keep endpoint structures consistent
* Use appropriate HTTP methods
* Return meaningful status codes
* Maintain consistent response formats

---

### Reflection

Designing APIs properly from the start reduces technical debt and improves long‑term scalability. Today’s learning helped me understand how thoughtful API design leads to better system architecture and easier integrations.
