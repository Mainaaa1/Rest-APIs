# Week 9 – REST APIs

## Day 4: Rate Limiting (12 Mar 2026)

### Overview

Today I studied **rate limiting**, a critical mechanism used to control how many requests a client can make to an API within a given timeframe.

Rate limiting protects APIs from abuse, ensures fair usage among clients, and helps maintain system stability under high traffic conditions.

---

### Why Rate Limiting is Important

Without rate limiting, APIs are vulnerable to:

* Abuse from malicious users or bots
* Denial-of-Service (DoS) attacks
* Excessive resource consumption
* Performance degradation for legitimate users

Rate limiting ensures that no single client can overwhelm the system.

---

### Common Rate Limiting Strategies

#### 1. Fixed Window

Limits requests within a fixed time window.

Example:

```
100 requests per minute
```

If a user exceeds this limit, further requests are blocked until the next window.

---

#### 2. Sliding Window

Tracks requests over a rolling time period instead of fixed intervals.

Advantages:

* More accurate control
* Prevents bursts at window boundaries

---

#### 3. Token Bucket

Clients are given tokens that represent allowed requests.

* Each request consumes a token
* Tokens refill over time

Advantages:

* Allows short bursts of traffic
* Smooth rate control

---

#### 4. Leaky Bucket

Requests are processed at a fixed rate.

* Incoming requests are queued
* Excess requests are dropped if the queue is full

---

### HTTP Response for Rate Limiting

When a client exceeds the allowed rate, the API returns:

```
HTTP 429 Too Many Requests
```

Example response headers:

```
X-RateLimit-Limit: 100
X-RateLimit-Remaining: 0
X-RateLimit-Reset: 1710000000
```

These headers help clients understand their usage and when they can retry.

---

### Implementation Approaches

Rate limiting can be implemented using:

* API gateways
* Middleware in backend frameworks
* Reverse proxies (e.g., Nginx)
* In-memory stores like Redis for tracking request counts

---

### Best Practices

Key lessons learned:

* Set reasonable limits based on use case
* Differentiate limits for authenticated vs unauthenticated users
* Provide clear feedback via headers
* Allow higher limits for trusted clients
* Log and monitor usage patterns

---

### Reflection

Rate limiting is essential for building reliable and secure APIs. It ensures fair usage while protecting infrastructure from overload and abuse. Implementing it correctly is a key part of production-ready API design.
