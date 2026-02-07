# API Design Notes

Guidelines for designing clean, consistent, and usable REST APIs.

---

## URL Structure

### Use Nouns, Not Verbs

URLs should represent resources (things), not actions.

| ❌ Bad | ✅ Good |
|--------|---------|
| `/getUsers` | `/users` |
| `/createUser` | `/users` (with POST) |
| `/deleteUser/42` | `/users/42` (with DELETE) |
| `/updateUserEmail` | `/users/42` (with PATCH) |

The HTTP method indicates the action; the URL indicates the resource.

### Use Plural Nouns

Be consistent — always use plural for collections.

| ❌ Inconsistent | ✅ Consistent |
|-----------------|---------------|
| `/user/42` | `/users/42` |
| `/post/1/comment` | `/posts/1/comments` |

### Use Kebab-Case for Multi-Word URLs

```
✅ /user-profiles
✅ /order-items
❌ /userProfiles
❌ /user_profiles
```

### Nest Resources Logically

Show relationships through URL structure:

```
/users/42/posts          # Posts by user 42
/users/42/posts/7        # Post 7 by user 42
/posts/7/comments        # Comments on post 7
```

But don't nest too deeply (max 2-3 levels):

```
❌ /users/42/posts/7/comments/3/likes/1
✅ /comments/3/likes  or  /likes/1
```

---

## HTTP Methods

### CRUD Mapping

| CRUD Operation | HTTP Method | URL Example | Description |
|----------------|-------------|-------------|-------------|
| **C**reate | POST | `/users` | Create a new user |
| **R**ead (list) | GET | `/users` | Get all users |
| **R**ead (single) | GET | `/users/42` | Get user 42 |
| **U**pdate (full) | PUT | `/users/42` | Replace user 42 entirely |
| **U**pdate (partial) | PATCH | `/users/42` | Update some fields of user 42 |
| **D**elete | DELETE | `/users/42` | Delete user 42 |

### PUT vs PATCH

**PUT** — Replace the entire resource (must send all fields)
```json
PUT /users/42
{
  "name": "Jane Doe",
  "email": "jane@example.com",
  "age": 30,
  "role": "admin"
}
```

**PATCH** — Update only specified fields
```json
PATCH /users/42
{
  "email": "newemail@example.com"
}
```

### Idempotency

An operation is **idempotent** if calling it multiple times produces the same result.

| Method | Idempotent? | Explanation |
|--------|-------------|-------------|
| GET | ✅ Yes | Reading doesn't change anything |
| PUT | ✅ Yes | Same data = same result |
| DELETE | ✅ Yes | Deleting twice = still deleted |
| POST | ❌ No | Creates new resource each time |
| PATCH | ⚠️ Depends | Usually yes, but can vary |

---

## Request & Response Format

### Use JSON

JSON is the standard format for REST APIs.

**Request:**
```json
POST /users
Content-Type: application/json

{
  "name": "Jane Doe",
  "email": "jane@example.com"
}
```

**Response:**
```json
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": 42,
  "name": "Jane Doe",
  "email": "jane@example.com",
  "created_at": "2026-01-15T10:30:00Z"
}
```

### Use Consistent Field Names

Pick a naming convention and stick to it:

| Convention | Example | Common in |
|------------|---------|-----------|
| snake_case | `user_name`, `created_at` | Python, Ruby |
| camelCase | `userName`, `createdAt` | JavaScript |

**Recommendation:** Use `snake_case` for Python backends (matches Python conventions).

### Timestamps

Use ISO 8601 format:

```json
{
  "created_at": "2026-01-15T10:30:00Z",
  "updated_at": "2026-01-15T14:45:30Z"
}
```

---

## Status Codes

### Success Codes (2xx)

| Code | Meaning | When to Use |
|------|---------|-------------|
| `200 OK` | Success | GET, PUT, PATCH succeeded |
| `201 Created` | Resource created | POST succeeded |
| `204 No Content` | Success, no body | DELETE succeeded |

### Client Error Codes (4xx)

| Code | Meaning | When to Use |
|------|---------|-------------|
| `400 Bad Request` | Invalid input | Malformed JSON, validation failed |
| `401 Unauthorized` | Not authenticated | Missing or invalid token |
| `403 Forbidden` | Not authorized | Authenticated but not allowed |
| `404 Not Found` | Resource doesn't exist | ID not in database |
| `409 Conflict` | Conflict with current state | Duplicate email, etc. |
| `422 Unprocessable Entity` | Validation error | Valid JSON but invalid data |

### Server Error Codes (5xx)

| Code | Meaning | When to Use |
|------|---------|-------------|
| `500 Internal Server Error` | Server broke | Unhandled exception |
| `503 Service Unavailable` | Temporarily down | Maintenance, overload |

---

## Error Responses

### Consistent Error Format

Always return errors in a consistent structure:

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid input data",
    "details": [
      {
        "field": "email",
        "message": "Invalid email format"
      },
      {
        "field": "age",
        "message": "Must be a positive number"
      }
    ]
  }
}
```

### Include Helpful Information

- **What went wrong** — Clear message
- **Where it went wrong** — Which field, if applicable
- **How to fix it** — What the correct format should be

**Bad:**
```json
{"error": "Bad request"}
```

**Good:**
```json
{
  "error": {
    "code": "INVALID_EMAIL",
    "message": "The email address is not valid",
    "details": {
      "field": "email",
      "value": "not-an-email",
      "expected": "Valid email format (e.g., user@example.com)"
    }
  }
}
```

---

## Query Parameters

Use query parameters for filtering, sorting, and pagination.

### Filtering

```
GET /users?role=admin
GET /users?status=active&role=admin
GET /posts?author_id=42
```

### Sorting

```
GET /users?sort=name              # Ascending by name
GET /users?sort=-created_at       # Descending by created_at
GET /users?sort=role,-name        # By role, then by name descending
```

### Pagination

```
GET /users?page=2&per_page=20
GET /users?offset=40&limit=20
```

**Response should include pagination info:**

```json
{
  "data": [...],
  "pagination": {
    "page": 2,
    "per_page": 20,
    "total": 150,
    "total_pages": 8
  }
}
```

### Searching

```
GET /users?q=jane
GET /users?search=doe
```

---

## Versioning

APIs evolve. Version them to avoid breaking existing clients.

### URL Versioning (Recommended for simplicity)

```
/api/v1/users
/api/v2/users
```

### Header Versioning

```
GET /users
Accept: application/vnd.myapp.v1+json
```

**Recommendation:** Start with `/api/v1/` in your URLs. It's simple and clear.

---

## Authentication

### Common Methods

| Method | How it works | Use case |
|--------|--------------|----------|
| **API Key** | Key in header or query param | Simple internal APIs |
| **Bearer Token** | Token in Authorization header | Most common for user auth |
| **OAuth 2.0** | Complex token exchange | Third-party integrations |

### Bearer Token Example

```http
GET /users/me
Authorization: Bearer eyJhbGciOiJIUzI1NiIs...
```

### Best Practices

- Never put tokens in URLs (they get logged)
- Use HTTPS for all authenticated endpoints
- Implement token expiration and refresh
- Store secrets in environment variables, not code

---

## Best Practices Summary

### Do

✅ Use nouns for URLs, verbs via HTTP methods  
✅ Use plural nouns consistently  
✅ Return appropriate status codes  
✅ Use consistent error formats  
✅ Version your API from the start  
✅ Document your API  
✅ Validate input data  
✅ Use HTTPS  

### Don't

❌ Put verbs in URLs (`/getUser`)  
❌ Use inconsistent naming (`/users` vs `/User`)  
❌ Return `200 OK` for errors  
❌ Expose sensitive data in responses  
❌ Forget pagination for list endpoints  
❌ Nest URLs too deeply  
❌ Store secrets in code  

---

## Quick Reference

### URL Patterns

```
GET    /resources          # List all
GET    /resources/:id      # Get one
POST   /resources          # Create
PUT    /resources/:id      # Replace
PATCH  /resources/:id      # Update
DELETE /resources/:id      # Delete
```

### Common Status Codes

```
200 - OK (success)
201 - Created
204 - No Content (deleted)
400 - Bad Request
401 - Unauthorized
403 - Forbidden
404 - Not Found
500 - Server Error
```

### Request Headers

```
Content-Type: application/json
Authorization: Bearer <token>
Accept: application/json
```
