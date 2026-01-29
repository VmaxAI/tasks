# Bug Report

### Describe the bug

After a recent update, the markdown parser is throwing unexpected errors when processing GitHub Flavored Markdown content. The parser crashes with an unhandled error during normal operation, making it impossible to render any markdown content.

### Reproduction

```js
import remarkGfm from './vendor/remark-gfm@4.0.0.js';

const markdown = `
# Test Document

This is a simple markdown document with GFM features.

- Item 1
- Item 2
`;

// This now throws an error
const result = parseMarkdown(markdown);
```

### Expected behavior

The markdown should be parsed successfully without throwing any errors. The parser should handle standard GFM syntax without crashing.

### System Info
- remark-gfm version: 4.0.0
- Node version: Latest

---
Repository: /testbed
