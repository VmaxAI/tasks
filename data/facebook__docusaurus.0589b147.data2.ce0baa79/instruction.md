# Bug Report

### Describe the bug

I'm experiencing an issue with MDX parsing where text content is being consumed incorrectly at break points. When the parser encounters a break condition (like end of input or certain delimiters), it seems to consume an extra character before transitioning states, which causes the parser to skip or mishandle content.

### Reproduction

```js
// Parsing MDX content with text followed by a break
const mdxContent = `
Some text content here
Another line
`;

// The parser appears to consume characters at break boundaries incorrectly
// resulting in malformed output or missing content
```

### Expected behavior

The parser should properly handle text data at break points without consuming additional characters. Text content should be preserved exactly as written, and state transitions should happen cleanly without affecting the character stream.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: Latest

---
Repository: /testbed
