## Front-End Foundations

### Understand how the Web works at a high level

* HTTP: requests, responses, status codes (200, 404, 500 etc.), what happens when you type a URL.
* Browser rendering basics: HTML + CSS + JS; what the browser does.
* Domain, DNS, hosting, what “static site” means.
* Tools: Getting comfortable with the terminal/command line. (Optional but useful.)
* Resources often list this as part of “internet fundamentals.”

### Version control essentials

* Git basics: init, clone, commit, push, pull, branches.
* Using GitHub or other remote repo to back up and share your code.

### HTML & CSS

* HTML: semantic markup; structure of pages; headings, paragraphs, images, links, lists, forms (basic).
* CSS: selectors; box model; layout (Flexbox, Grid); colors, typography; spacing.
* Responsive web design: media queries, fluid layouts so site works on phones/tablets/desktop.
* CSS fundamentals like margin, padding, display, positioning.

### Basic JavaScript

* What JS is, how to include it in pages.
* DOM manipulation: select elements, change content/style, respond to events (clicks, form submits).
* Simple things: variables, functions, loops, conditionals.
* Modern JS (ES6+): let/const, arrow functions, modules. (Good enough for static sites where you might have some dynamic behavior.)

### Browser tools / Debugging

* Using browser dev tools (inspect element, console, network tab).
* Checking responsiveness, debugging JS errors.

### Accessibility, UX basics, SEO basics

* Make sure content is readable, use alt text for images, proper semantic HTML tags etc.
* Basic performance: minimize large images, efficient CSS.
* Meta tags, title tags, structuring markup so that search engines can parse it.

### Putting it together: build a static site

* Choose a simple project: e.g. personal portfolio, a small business page, blog-like page but static.
* Host it (GitHub Pages, Netlify, or cheap static hosting) so it’s accessible online.
* Validate HTML/CSS; test on different devices/screen sizes.

---

## Stage 2: Front-End Intermediate (optional depending on how dynamic you want)

Once you have a static site working and feel comfortable with the basics, these are useful:

* Fetching data from external sources (REST API) via JavaScript (e.g. `fetch`)
* More JavaScript: Promises, async/await
* Client-side form validation
* State management basics if the site grows
* Maybe learn a front-end framework/library (React, Vue, Angular) if you plan for richer UI.

---

## Stage 3: Backend Foundations with Python

After front end, you switch to backend. Here are the steps, order, and depth:

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

* Understand WSGI / ASGI (concepts: how requests get handled). ([HackMD][1])
* Basic routing: different URLs map to different responses.

### Pick a Python web framework (micro first, then maybe full)

* Start with something lightweight: **Flask** is a good choice. You can build simple APIs, serve templates, etc.
* Later optionally move to **Django**, which gives you more built-in tools (ORM, admin panel, project scaffolding).

### Databases / Data persistence

* Relational databases: SQL basics — SELECT, INSERT, UPDATE, DELETE; joins; schema design.
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

## Stage 4: Full-Stack Integration, Advanced Topics

After you have both front end and backend basics, bring them together and deepen your understanding.

### Connecting front and backend

* Fetch data from backend APIs in front end (AJAX / fetch etc.).
* Handling CORS.
* Templating (if using server-rendered HTML) vs Single Page App (SPA) patterns.

### Stateful features

* Forms that submit data to backend.
* User sessions, authentication / user accounts.

### Deployment of full stack app

* Serve front end + backend in production.
* Continuous Integration / Continuous Deployment (CI/CD).
* SSL / HTTPS.

### Performance & Scaling Basics

* Caching (in memory, at server, client side).
* Database indexing, query optimization.
* Static asset optimization (minify CSS/JS, compress images).

### Maintainability, Code Architecture

* Clean architecture / separation of concerns.
* Modular code.
* Documentation.

---

## Suggested Timeline / Milestones

(to keep you honest and not overwhelmed)

* **Weeks 1-2**: Web fundamentals + HTML/CSS + a small static page.
* **Weeks 3-4**: JS basics + making site interactive + responsive design.
* **Week 5**: Put together first static site; deploy it live.
* **Weeks 6-7**: Python basics + simple server (Flask).
* **Weeks 8-10**: Backend: data persistence + REST API + connecting front end to backend.
* **Weeks 11-12**: Add authentication, deploy backend + front end, learn basic security.

You might stretch or shrink time depending on how many hours per week you can invest.

---
