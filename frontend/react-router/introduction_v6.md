# React Router

**Note**: This file covers version 6. The current stable version of react router.

## Introduction to React Router

React Router is a standard library for routing in React applications. Routing refers to the process of keeping the browser URL in sync with what is rendered on the page. React Router allows you to build a single-page application (SPA) with navigation that does not cause a full page reload.

---

## Installation

React Router has different packages for web, native, and other environments. For web development, install `react-router-dom`.

```bash
npm install react-router-dom
```

or

```bash
yarn add react-router-dom
```

---

## Core Components

### BrowserRouter

`BrowserRouter` is a wrapper component that uses the HTML5 history API to keep your UI in sync with the URL. You should place it at the root of your application, usually around the main `App` component.

```jsx
import { BrowserRouter } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      {/* Your routes and components go here */}
    </BrowserRouter>
  );
}
```

### Routes and Route

`Routes` is a component that looks through its children `Route` elements and renders the first one whose path matches the current URL.

`Route` defines a mapping between a URL path and a component. It has two main props:
- `path`: the URL pattern to match.
- `element`: the component to render when the path matches.

```jsx
import { Routes, Route } from 'react-router-dom';
import Home from './Home';
import About from './About';

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}
```

### Link

`Link` is a component that allows navigation to a different route without reloading the page. It replaces the standard `<a>` tag and uses the `to` prop to specify the target path.

```jsx
import { Link } from 'react-router-dom';

function Navigation() {
  return (
    <nav>
      <Link to="/">Home</Link>
      <Link to="/about">About</Link>
    </nav>
  );
}
```

### NavLink

`NavLink` is a special version of `Link` that adds styling attributes when the link matches the current URL. It provides an `active` class by default.

```jsx
import { NavLink } from 'react-router-dom';

<NavLink to="/about" className={({ isActive }) => isActive ? 'active' : ''}>
  About
</NavLink>
```

---

## Navigation and Hooks

React Router provides several hooks for accessing routing state and performing navigation programmatically.

### useNavigate

`useNavigate` returns a function that lets you navigate programmatically, for example after form submission.

```jsx
import { useNavigate } from 'react-router-dom';

function Login() {
  const navigate = useNavigate();

  const handleSubmit = () => {
    // Perform login logic
    navigate('/dashboard');
  };

  return <button onClick={handleSubmit}>Login</button>;
}
```

### useParams

`useParams` returns an object of key-value pairs of URL parameters. This is useful for dynamic routes.

```jsx
// Route definition: <Route path="/user/:userId" element={<User />} />

import { useParams } from 'react-router-dom';

function User() {
  const { userId } = useParams();
  return <div>Viewing user: {userId}</div>;
}
```

### useLocation

`useLocation` returns the current location object, which contains information about the URL including pathname, search query, and state.

```jsx
import { useLocation } from 'react-router-dom';

function CurrentPage() {
  const location = useLocation();
  return <div>You are at: {location.pathname}</div>;
}
```

---

## Nested Routes

Nested routes allow you to render child components inside parent components based on URL segments. This is done by placing `Outlet` components in the parent layout.

```jsx
import { Routes, Route, Outlet } from 'react-router-dom';

function Layout() {
  return (
    <div>
      <header>My App</header>
      <Outlet /> {/* Child routes render here */}
      <footer>Footer</footer>
    </div>
  );
}

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Layout />}>
          <Route index element={<Home />} />          // index means path "/"
          <Route path="about" element={<About />} />  // path "/about"
          <Route path="contact" element={<Contact />} /> // path "/contact"
        </Route>
      </Routes>
    </BrowserRouter>
  );
}
```

---

## Handling 404 Not Found

To handle unknown routes, create a `Route` without a `path` prop or with a `path="*"`. This catches all unmatched URLs.

```jsx
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/about" element={<About />} />
  <Route path="*" element={<NotFound />} />
</Routes>
```

---

## Query Parameters

Query parameters are not part of the route path. They can be accessed via `useLocation` and parsed using `URLSearchParams`.

```jsx
import { useLocation } from 'react-router-dom';

function Search() {
  const location = useLocation();
  const queryParams = new URLSearchParams(location.search);
  const query = queryParams.get('q');

  return <div>Search term: {query}</div>;
}
```

---

## Full Example

Below is a complete working example combining the above concepts.

```jsx
// App.js
import { BrowserRouter, Routes, Route, Link, Outlet } from 'react-router-dom';

function Layout() {
  return (
    <div>
      <nav>
        <Link to="/">Home</Link>
        <Link to="/products">Products</Link>
      </nav>
      <Outlet />
    </div>
  );
}

function Home() {
  return <h1>Home Page</h1>;
}

function Products() {
  return <h1>Products Page</h1>;
}

function NotFound() {
  return <h1>404 - Page Not Found</h1>;
}

export default function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Layout />}>
          <Route index element={<Home />} />
          <Route path="products" element={<Products />} />
          <Route path="*" element={<NotFound />} />
        </Route>
      </Routes>
    </BrowserRouter>
  );
}
```

---
