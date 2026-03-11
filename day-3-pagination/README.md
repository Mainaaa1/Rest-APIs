# Week 9 – REST APIs

## Day 3: Pagination (11 Mar 2026)

### Overview

Today I explored **pagination in REST APIs**, a technique used to divide large datasets into smaller, manageable chunks when returning results from an API.

Without pagination, endpoints that return thousands of records can become slow, consume excessive bandwidth, and create performance issues for both servers and clients.

Pagination ensures that APIs remain efficient, scalable, and responsive when working with large datasets.

---

### Why Pagination is Important

When an API endpoint returns a very large collection of data, several issues can arise:

* Slow response times
* Increased server load
* Higher memory consumption
* Poor user experience in client applications

Pagination solves these problems by returning only a subset of results per request.

Example:

Instead of returning **10,000 records**, an API might return **10 or 20 records per request**.

---

### Offset-Based Pagination

Offset pagination is one of the most common pagination strategies.

It works by specifying a page number and the number of items per page.

Example request:

```
GET /api/products?page=2&limit=10
```

This means:

* Return page 2
* Return 10 items per page

Example response:

```json
{
  "page": 2,
  "limit": 10,
  "total": 120,
  "data": [
    { "id": 11, "name": "Product A" },
    { "id": 12, "name": "Product B" }
  ]
}
```

Advantages:

* Simple to implement
* Easy for clients to understand

Disadvantages:

* Can become inefficient with very large datasets
* Large offsets may slow database queries

---

### Cursor-Based Pagination

Cursor pagination uses a **pointer (cursor)** instead of a numeric page index.

The cursor represents the position in the dataset.

Example request:

```
GET /api/products?cursor=eyJpZCI6MTB9
```

Example response:

```json
{
  "nextCursor": "eyJpZCI6MjB9",
  "data": [
    { "id": 11, "name": "Product A" },
    { "id": 12, "name": "Product B" }
  ]
}
```

Advantages:

* Faster for large datasets
* Avoids performance issues with large offsets

Disadvantages:

* Slightly more complex to implement
* Harder to manually navigate pages

Cursor pagination is often used in **large-scale APIs** and **real-time systems**.

---

### Limit-Based Pagination

Another simple method is limiting the number of records returned.

Example:

```
GET /api/products?limit=20
```

This simply returns the first 20 results.

While simple, it does not provide navigation between pages.

---

### Pagination Metadata

Good APIs include metadata to help clients understand the dataset.

Example response structure:

```json
{
  "page": 1,
  "limit": 10,
  "total": 100,
  "totalPages": 10,
  "data": []
}
```

Common metadata fields include:

* current page
* number of results per page
* total number of records
* total number of pages

This information allows frontends to build pagination controls easily.

---

### Pagination Best Practices

Key lessons learned today:

* Always paginate endpoints returning large collections
* Provide metadata to help clients navigate results
* Use reasonable default limits
* Prevent extremely large page sizes
* Consider cursor pagination for large datasets

Example limit protection:

```
Maximum limit per request: 100
```

---

### Reflection

Pagination is a fundamental technique for building scalable APIs. By limiting how much data is returned in a single request, APIs remain performant and easier for clients to consume. Understanding the trade-offs between offset and cursor pagination is essential when designing production systems.
