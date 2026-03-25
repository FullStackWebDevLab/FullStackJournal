## REST API

### What is a REST API?

**API** stands for Application Programming Interface. It is a set of rules that allows one software application to talk to another. Think of it as a waiter in a restaurant: you (the client) give an order, and the waiter (the API) tells the kitchen (the server) what to do, then brings the result back to you.

**REST** stands for Representational State Transfer. It is a set of architectural principles for building APIs. A REST API uses these principles to create a reliable, predictable, and scalable way for systems to communicate over the internet, typically using HTTP, the same protocol web browsers use.

In simple terms, a REST API exposes **resources** (such as users, products, or articles) at specific **endpoints** (URLs). You perform actions on these resources using standard **HTTP methods**.

---

### Core Principles of REST

To be considered RESTful, an API should follow these key principles:

1.  **Client-Server Separation:** The client (front-end application) and the server (back-end database and logic) are independent. They only interact through the API. This allows you to change the front-end without affecting the back-end, and vice versa.

2.  **Statelessness:** The server does not remember the client’s previous actions. Each request from the client must contain all the information the server needs to process it. This makes the system more reliable and easier to scale.

3.  **Cacheability:** Responses from the server should indicate whether they can be cached (stored for later use) by the client. Caching improves performance by reducing the number of direct requests to the server.

4.  **Uniform Interface:** REST APIs use a consistent and predictable structure. This is the most important principle for a developer. It means:
    - **Resources are identified by URLs.** For example, `/users/` is for users.
    - **HTTP methods define the action.**
    - **Responses contain hypermedia links** (HATEOAS - Hypermedia as the Engine of Application State) to guide the client on what actions are possible next.

---

### HTTP Methods and Status Codes

REST APIs use standard HTTP methods to perform operations, often referred to as CRUD (Create, Read, Update, Delete).

| HTTP Method | Action | Description |
| :--- | :--- | :--- |
| **GET** | Read | Retrieve one or more resources. This does not change data. |
| **POST** | Create | Create a new resource. The server typically returns the new resource's ID. |
| **PUT** | Update | Replace an entire existing resource. |
| **PATCH** | Update | Partially modify an existing resource. |
| **DELETE** | Delete | Remove a resource. |

The server also returns **HTTP status codes** with every response to indicate the result:

- **2xx Success:** The request succeeded.
    - `200 OK` (for successful `GET`, `PUT`, `PATCH`)
    - `201 Created` (for successful `POST`)
    - `204 No Content` (for successful `DELETE`)
- **4xx Client Error:** The error is on the client's side.
    - `400 Bad Request` (the request is malformed)
    - `401 Unauthorized` (authentication is required)
    - `403 Forbidden` (authenticated but not allowed)
    - `404 Not Found` (the resource does not exist)
- **5xx Server Error:** The error is on the server's side. `500 Internal Server Error` is the most common.

---

### REST API Structure

A REST API organizes data into **resources**. The URL structure reflects this.

- **Collection:** `/articles/`
- **Individual item:** `/articles/42/`

#### Common Endpoint Examples

- `GET /articles/` — Retrieves a list of all articles.
- `POST /articles/` — Creates a new article.
- `GET /articles/42/` — Retrieves the details of article number 42.
- `PUT /articles/42/` — Updates the entire article number 42.
- `DELETE /articles/42/` — Deletes article number 42.

---

### Building a REST API with Django

Django is a high-level Python web framework. While Django itself is designed for full-stack web applications, it has excellent tools for building REST APIs. The most common approach is to use **Django REST Framework (DRF)** .

DRF is a powerful library that simplifies the process of creating RESTful APIs. It handles serialization (converting complex data types like Django models to JSON), authentication, permissions, and view logic.

#### Example: A Simple Article API

Let us create a simple API for an `Article` model.

**1. Model (in `models.py`)**
First, we define the data structure.
```python
from django.db import models

class Article(models.Model):
    title = models.CharField(max_length=100)
    content = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)

    def __str__(self):
        return self.title
```

**2. Serializer (in `serializers.py`)**
A serializer converts the Python model into JSON (the common data format for APIs) and validates incoming data.
```python
from rest_framework import serializers
from .models import Article

class ArticleSerializer(serializers.ModelSerializer):
    class Meta:
        model = Article
        fields = ['id', 'title', 'content', 'created_at']
```

**3. ViewSet (in `views.py`)**
A ViewSet groups together the logic for handling standard actions like `list`, `create`, `retrieve`, `update`, and `destroy`. DRF provides a `ModelViewSet` that automatically implements all these actions.
```python
from rest_framework import viewsets
from .models import Article
from .serializers import ArticleSerializer

class ArticleViewSet(viewsets.ModelViewSet):
    queryset = Article.objects.all()  # The set of data this view manages
    serializer_class = ArticleSerializer  # The serializer to use
```

**4. URL Configuration (in `urls.py`)**
Finally, we connect the ViewSet to URLs. The `DefaultRouter` automatically creates the standard RESTful URL patterns (`/articles/` and `/articles/<id>/`).
```python
from django.urls import path, include
from rest_framework.routers import DefaultRouter
from .views import ArticleViewSet

router = DefaultRouter()
router.register(r'articles', ArticleViewSet)  # Register the viewset

urlpatterns = [
    path('', include(router.urls)),  # Include the generated URLs
]
```

With this minimal code, you now have a fully functional REST API. You can:
- `GET http://127.0.0.1:8000/articles/` to list all articles.
- `POST http://127.0.0.1:8000/articles/` with JSON data to create a new article.
- `GET http://127.0.0.1:8000/articles/1/` to retrieve a single article.
- `PUT http://127.0.0.1:8000/articles/1/` to update it.
- `DELETE http://127.0.0.1:8000/articles/1/` to delete it.

---

### Important Considerations for Using REST APIs

1.  **Authentication:** For public APIs, you must control who can access the data. Common methods include:
    - **API Keys:** A unique key passed in the request header.
    - **Token Authentication:** The client sends a username and password to a login endpoint to receive a token, then uses that token for subsequent requests.
    - **JWT (JSON Web Tokens):** A self-contained token that holds user information.

2.  **Data Format:** The standard format for REST APIs is **JSON** (JavaScript Object Notation). It is lightweight, readable, and language-agnostic.

3.  **Versioning:** As your API evolves, you may need to make breaking changes. It is a best practice to version your API in the URL, such as `/api/v1/articles/` and `/api/v2/articles/`.

4.  **Documentation:** A good API requires clear documentation. Tools like **Swagger/OpenAPI** can automatically generate interactive documentation from your DRF code, making it easy for other developers to understand and use your API.

---
