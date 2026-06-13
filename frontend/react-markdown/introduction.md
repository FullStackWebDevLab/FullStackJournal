# `react-markdown`

`react-markdown` is a React component that allows you to reander Markdown text as React elements. It does not use the `dangerouslySetInnerHTML` property to prevent Cross-Site Scripting (XSS) attacks.

## Installation

```bash
npm install react-markdown
```

---

## Basic Usage

```jsx
import React from 'react';
import ReactMarkdown from 'react-markdown';

const markdownText = `
# This is a heading

This is a paragraph with **bold** and *italic* text.

Here is a list:
- Item one
- Item two
`;

function MyMarkdownRenderer() {
  return <ReactMarkdown>{markdownText}</ReactMarkdown>;
}

export default MyMarkdownRenderer;
```

The `<ReactMarkdown>` component parses this text and outputs the corresponding HTML elements.

---

## Advanced Configuration

You can control how Markdown is parsed and how the final output is rendered using props and plugins.

### Example Props

+ `skipHtml` (`boolean`): When set to `true`, it ignores any raw HTML found in the Markdown. Defaults to `false`.
+ `allowedElements` (`string[]`): An array of tag names that are allowed to be rendered. Defaults to all elements.
+ `disallowedElements` (`string[]`): An array of tag names that are not allowed to be rendered. Defaults to an empty list.

### Plugins

The library can be extended with plugins to support additional markdown syntax. Two common types of plugins are `remarkPlugins` (for parsing) and `rehypePlugins` (for transforming the output).

For example, to render GitHub Flavored Markdown (GFM), you can install and use the `remark-gfm` plugin.

Install the plugin.

```bash
npm install remark-gfm
```

Add it to the `remarkPlugins` prop:

```jsx
import React from 'react';
import ReactMarkdown from 'react-markdown';
import remarkGfm from 'remark-gfm';

const markdownWithTable = `
| Header 1 | Header 2 |
| -------- | -------- |
| Cell 1   | Cell 2   |
`;

function GFMExample() {
  return (
    <ReactMarkdown remarkPlugins={[remarkGfm]}>
      {markdownWithTable}
    </ReactMarkdown>
  );
}
```

---

## Customizing Components

`react-markdown` allows you to override the default HTML tags with your own custom React components, through the `components` prop.

```jsx
import React from 'react';
import ReactMarkdown from 'react-markdown';

const markdownWithLink = 'Link to [Example](https://www.example.com).';

function CustomLinkRenderer() {
  const components = {
    a: ({ href, children }) => (
      <a href={href} target="_blank" rel="noopener noreferrer">
        {children}
      </a>
    ),
  };

  return (
    <ReactMarkdown components={components}>
      {markdownWithLink}
    </ReactMarkdown>
  );
}
```

In this example, any link rendered by `react-markdown` will now receive the `target="_blank"` and `rel="noopener noreferre"` attributes.

---
