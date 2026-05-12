# `<StrictMode>`

Strict Mode enable extra development-only checks for the entire component tree inside the `<StrictMode>` component. The following behaviors are enabled:

+ Your components will re-render an extra time to find bugs caused by impure rendering.
+ Your components will re-run Effects an extra time to find bugs caused by missing Effect cleanup.
+ Your components will re-run refs callbacks an extra time to find bugs caused by missing ref cleanup.
+ Your components will be checked for usage of deprecated APIs.

**Note**: `<StrictMode>` does not accept any props.

---

## Enabling Strict Mode

To enable strict mode for your entire app, wrap your root component with `<StrictMode>` when you render it.

```react
import { StrictMode } from 'react';
import { createRoot } from 'react-dom/client';

const root = createRoot(document.getElementById('root'));
root.render(
  <StrictMode>
    <App />
  </StrictMode>
);
```

**Note:** There is no way to opt out of strict mode inside a tree wrapped in `<StrictMode>`.

You can also enable strict mode for any part of your application:

```react
import { StrictMode } from 'react';

function App() {
  return (
    <>
      <Header />
      <StrictMode>
        <main>
          <Sidebar />
          <Content />
        </main>
      </StrictMode>
      <Footer />
    </>
  );
}
```

In this example, strict mode checks will not run against the `Header` and `Footer` components.

---
