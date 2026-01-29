# Bug Report

### Describe the bug

I'm experiencing an issue with markdown parsing where line endings are not being recognized correctly. This is causing unexpected behavior when processing markdown content with different types of line breaks.

### Reproduction

```js
// When parsing markdown with line endings
const markdown = `
First line
Second line
Third line
`;

// The parser fails to properly detect line endings
// and treats the content as a single continuous line
```

### Expected behavior

The parser should correctly identify line ending characters (newlines, carriage returns, etc.) and treat them as separate lines. Each line should be processed independently.

### Additional context

This seems to affect multi-line markdown content. Single-line content appears to work fine, but anything with multiple lines gets concatenated together incorrectly.

---
Repository: /testbed
