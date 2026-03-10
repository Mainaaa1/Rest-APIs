# Week 9 – REST APIs

## Day 2: API Versioning (10 Mar 2026)

### Overview

Today I focused on API versioning, which allows APIs to evolve without breaking existing client applications. Once an API is used by external systems, changing response structures or endpoint behavior can cause failures. Versioning provides a structured way to introduce improvements while maintaining backward compatibility.

---

### Why API Versioning Matters

APIs act as contracts between services and their consumers. When the contract changes, older clients may stop working. Versioning helps manage these changes safely.

Key benefits:

* Maintains backward compatibility
* Enables controlled API evolution
* Prevents breaking client applications
* Allows gradual migration to newer versions

Example scenario:

Original response:

```json
{
  "id": 1,
  "name": "John Doe"
}
```

Updated response with additional structure:

```json
{
  "id": 1,
  "firstName": "John",
  "lastName": "Doe",
  "email": "john@example.com"
}
```

Without versioning, this structural change could break clients expecting the original format.

---

### Common Versioning Strategies

#### 1. URL Versioning

The API version is included directly in the URL path.

Example:

```
/api/v1/users
/api/v2/users
```

Advantages:

* Simple to understand
* Easy to test
* Widely adopted

Disadvantages:

* Version appears in the URL path

Despite this, it remains the most common approach in production APIs.

---

#### 2. Query Parameter Versioning

The version is passed as a query parameter.

Example:

```
/api/users?version=1
```

Advantages:

* Cleaner URLs

Disadvantages:

* Less visible
* Harder to enforce across large APIs

---

#### 3. Header Versioning

The version is specified in the request header.

Example:

```
Accept: application/vnd.api.v1+json
```

Advantages:

* Keeps URLs clean
* Enables more advanced content negotiation

Disadvantages:

* Harder to test manually
* Less obvious for developers

---

### Recommended Approach

URL-based versioning is often preferred because it is explicit and easy to maintain.

Example:

```
GET /api/v1/products
```

When improvements are introduced:

```
GET /api/v2/products
```

Both versions can run in parallel while clients migrate.

---

### Versioning Best Practices

Important principles when implementing API versioning:

1. Only introduce a new version when breaking changes occur.
2. Avoid creating too many API versions.
3. Clearly document changes between versions.
4. Provide a deprecation timeline for older versions.
5. Maintain consistent behavior across versions whenever possible.

Example deprecation notice:

```
Warning: API v1 will be deprecated on 31 Dec 2026
```

---

### Example Versioned API Structure

```
/api
  /v1
    /users
    /orders
  /v2
    /users
    /orders
```

This structure allows teams to iterate on new API designs without affecting existing integrations.

---

### Reflection

API versioning is a critical practice for maintaining stable systems. As APIs grow and more applications depend on them, versioning ensures improvements can be delivered safely without disrupting existing users.
