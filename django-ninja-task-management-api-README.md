# Django Ninja Task Management API

**Schema-first REST API — type-safe, auto-documented, minimal boilerplate.**

## Overview

A task management REST API built with Django Ninja instead of Django REST Framework, favoring a schema-first, type-annotated approach. Request/response validation and API documentation are generated automatically from Python type hints, keeping the codebase lean while staying fully type-safe.

## Tech Stack

- **Django Ninja** — API framework (schema-first, Pydantic-based validation)
- **SQLite** — persistence layer
- **React** — frontend client

## Features

- Full CRUD for tasks (create, read, update, delete, mark complete)
- Type-annotated request/response schemas with automatic validation
- Auto-generated interactive API docs (OpenAPI/Swagger) with zero extra configuration
- React frontend consuming the API

## Getting Started

### Backend

#### Prerequisites

- Python 3.10+

## API Reference

Key endpoints (see `/api/docs` for the full interactive schema):

```
GET    /api/tasks/
POST   /api/tasks/
GET    /api/tasks/{id}/
PATCH  /api/tasks/{id}/
DELETE /api/tasks/{id}/
```

## Why Django Ninja

Compared to Django REST Framework, Django Ninja leans on Python type hints and Pydantic schemas directly, which cuts down on serializer boilerplate and gives auto-generated, always-accurate API docs for free.

## License

MIT
