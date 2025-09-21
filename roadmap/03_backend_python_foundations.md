# Backend Python Foundations

### Python basics

* Syntax: variables, types, control flow (if/else, loops).
* Functions, parameters, return values.
* Data structures: lists, dictionaries, sets, tuples.
* Modules, packages.
* File I/O.

### Intermediate Python / Good Practices

* Virtual environments, dependency management (venv, pip).
* Writing clean code: readability, naming, structure.
* Basic object-oriented programming: classes, inheritance, methods.
* Exception handling.

### Web server fundamentals

* Understand WSGI / ASGI (concepts: how requests get handled).
* Basic routing: different URLs map to different responses.

### Pick a Python web framework

* Under normal circumstances, you are adviced to start with a lightweight framework like **Flask**.
* To save time, you will jump straight to **Django**.

### Databases / Data persistence

* Relational databases: SQL basics; SELECT, INSERT, UPDATE, DELETE; joins; schema design.
* Use an ORM (e.g. SQLAlchemy with Flask, or Django’s ORM) so you can map objects to DB.
* Basic database operations: migrations, schema changes.

### APIs and server logic

* Build RESTful API endpoints: standard patterns (CRUD: Create, Read, Update, Delete).
* JSON, data serialization.
* Authentication & Authorization basics (login, sessions / tokens).

### Testing, debugging, error handling

* Unit tests (pytest, unittest).
* Error handling and logging.
* Debugging tools.

### Security basics

* Understand common web security issues (SQL injection, cross-site scripting (XSS), cross-site request forgery (CSRF)).
* How to mitigate them (input validation, escaping, using framework protections).

### Deployment & Operations

* How to host your backend: cloud servers, VPS, or PaaS (Heroku, AWS, digital ocean etc.).
* Web servers/proxies: Nginx, Gunicorn, etc.
* Environment variables, configurations for production vs development.
* Basic monitoring, logging in production.

---
