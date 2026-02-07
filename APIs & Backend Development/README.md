# APIs and Backend Development

This section introduces you to building web APIs — the backbone of modern applications. You'll learn how clients and servers communicate, and how to build your own API using Python and FastAPI.

---

## Learning Objectives

By the end of this section, you will be able to:

- Understand HTTP requests and responses
- Explain REST API principles and design patterns
- Build a CRUD API using FastAPI
- Handle authentication basics and environment variables
- Connect your API to a SQLite database
- Structure a backend project for maintainability

---

## Contents

| File | Description |
|------|-------------|
| [API_DESIGN_NOTES.md](./API_DESIGN_NOTES.md) | API structure, endpoints, naming conventions, best practices |
| [fastapi_crud_lab.ipynb](./fastapi_crud_lab.ipynb) | Hands-on lab: Build a basic CRUD API |
| [auth_basics_lab.ipynb](./auth_basics_lab.ipynb) | Hands-on lab: Authentication concepts and environment variables |
| [sqlite_lab.ipynb](./sqlite_lab.ipynb) | Hands-on lab: Add database persistence |
| [starter-project/](./starter-project/) | Clean FastAPI starter project |

---

## Prerequisites

Before starting, make sure you have:

- [ ] Python 3.10+ installed
- [ ] Basic Python knowledge (functions, dictionaries, classes)
- [ ] A code editor (VS Code recommended)
- [ ] (Optional) Completed the Git and Docker section

### Install Required Libraries

```bash
pip install fastapi uvicorn python-dotenv
```

Or use the starter project's requirements:

```bash
cd starter-project
pip install -r requirements.txt
```

---

## What is an API?

**API** stands for **Application Programming Interface**. It's a way for different software applications to communicate with each other.

### Real-World Analogy

Think of a restaurant:
- **You (client)** — Want food
- **Menu (API documentation)** — Shows what's available and how to order
- **Waiter (API)** — Takes your request to the kitchen and brings back food
- **Kitchen (server/database)** — Prepares the food

You don't need to know how the kitchen works — you just need to know how to order from the menu.

### Web APIs

Web APIs allow applications to communicate over the internet using HTTP:

```
[Your App] ──HTTP Request──▶ [API Server] ──▶ [Database]
                                   │
[Your App] ◀──HTTP Response── [API Server] ◀──┘
```

**Examples of APIs you use every day:**
- Weather apps fetch data from weather APIs
- Social media apps use APIs to post and retrieve content
- Payment systems use APIs to process transactions

---

## HTTP Basics

**HTTP** (HyperText Transfer Protocol) is the language of the web. Every API request has:

### HTTP Methods

| Method | Purpose | Example |
|--------|---------|---------|
| `GET` | Retrieve data | Get a list of users |
| `POST` | Create new data | Create a new user |
| `PUT` | Update existing data (full replacement) | Update a user's profile |
| `PATCH` | Update existing data (partial) | Update just a user's email |
| `DELETE` | Remove data | Delete a user |

### HTTP Status Codes

| Code | Meaning | When to use |
|------|---------|-------------|
| `200` | OK | Request succeeded |
| `201` | Created | Resource was created |
| `204` | No Content | Success, but nothing to return |
| `400` | Bad Request | Invalid input from client |
| `401` | Unauthorized | Authentication required |
| `403` | Forbidden | Authenticated but not allowed |
| `404` | Not Found | Resource doesn't exist |
| `500` | Internal Server Error | Something broke on the server |

### Anatomy of an HTTP Request

```http
POST /api/users HTTP/1.1
Host: api.example.com
Content-Type: application/json
Authorization: Bearer token123

{
  "name": "Jane Doe",
  "email": "jane@example.com"
}
```

- **Method:** POST (creating something)
- **Path:** /api/users (the endpoint)
- **Headers:** Metadata (content type, auth token)
- **Body:** The data being sent (JSON)

### Anatomy of an HTTP Response

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": 42,
  "name": "Jane Doe",
  "email": "jane@example.com",
  "created_at": "2026-01-15T10:30:00Z"
}
```

- **Status:** 201 Created (success, resource created)
- **Headers:** Metadata about the response
- **Body:** The data being returned (JSON)

---

## REST API Principles

**REST** (Representational State Transfer) is a set of conventions for designing web APIs.

### Key Principles

1. **Resources** — Everything is a resource (users, posts, products)
2. **URLs identify resources** — `/users/42` refers to user with ID 42
3. **HTTP methods define actions** — GET to read, POST to create, etc.
4. **Stateless** — Each request contains all needed information
5. **JSON for data** — Standard format for request/response bodies

### RESTful URL Examples

| Action | Method | URL |
|--------|--------|-----|
| List all users | GET | `/users` |
| Get user #42 | GET | `/users/42` |
| Create a user | POST | `/users` |
| Update user #42 | PUT | `/users/42` |
| Delete user #42 | DELETE | `/users/42` |
| Get user #42's posts | GET | `/users/42/posts` |

---

## What is FastAPI?

**FastAPI** is a modern Python web framework for building APIs. It's:

- **Fast** — One of the fastest Python frameworks
- **Easy** — Intuitive syntax, great for beginners
- **Automatic docs** — Generates interactive API documentation
- **Type-safe** — Uses Python type hints for validation

### Hello World in FastAPI

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Hello, World!"}

@app.get("/users/{user_id}")
def read_user(user_id: int):
    return {"user_id": user_id}
```

Run with:
```bash
uvicorn main:app --reload
```

Visit `http://localhost:8000/docs` to see automatic interactive documentation!

---

## Suggested Learning Path

1. **Read API Design Notes** — Understand conventions and best practices
2. **Complete FastAPI/CRUD Lab** — Build your first API
3. **Complete Auth Basics Lab** — Add authentication concepts
4. **Complete SQLite Lab** — Add database persistence
5. **Explore the Starter Project** — Use it as a template for your own projects

---

## External Resources

### FastAPI

- [FastAPI Official Documentation](https://fastapi.tiangolo.com/) — Excellent tutorials
- [FastAPI Tutorial](https://fastapi.tiangolo.com/tutorial/) — Step-by-step guide
- [Tiangolo YouTube](https://www.youtube.com/c/Tiangolo) — Video tutorials from the creator

### HTTP & REST

- [HTTP Status Dogs](https://httpstatusdogs.com/) — Fun way to remember status codes
- [RESTful API Design](https://restfulapi.net/) — REST principles explained
- [MDN HTTP Guide](https://developer.mozilla.org/en-US/docs/Web/HTTP) — Comprehensive HTTP reference

### Tools

- [Postman](https://www.postman.com/) — GUI tool for testing APIs
- [curl](https://curl.se/) — Command-line tool for HTTP requests
- [HTTPie](https://httpie.io/) — User-friendly command-line HTTP client

### Going Deeper

- [Full Stack FastAPI Template](https://github.com/tiangolo/full-stack-fastapi-template) — Production-ready template
- [SQLModel](https://sqlmodel.tiangolo.com/) — Database ORM by FastAPI creator
- [FastAPI Best Practices](https://github.com/zhanymkanov/fastapi-best-practices) — Community guide

---

## Common Questions

**Q: Why FastAPI instead of Flask or Django?**

FastAPI is newer and designed specifically for APIs. It has automatic documentation, built-in validation, and excellent performance. Flask is simpler but requires more manual work. Django is more full-featured but heavier for pure APIs.

**Q: Do I need to know async/await?**

No! FastAPI works with both regular functions and async functions. Start with regular functions and learn async later when you need it.

**Q: How is this different from frontend development?**

Frontend (React, HTML/CSS) is what users see and interact with. Backend (APIs, databases) is the "behind the scenes" logic and data storage. They communicate via APIs.

---
