# Bug Report

### Describe the bug

I'm experiencing an issue with markdown parsing where documents aren't being properly finalized. When processing markdown content, it seems like the flow isn't being closed correctly, which can lead to incomplete parsing or unexpected behavior.

### Reproduction

```js
// Create a markdown document with nested content
const markdown = `
# Title

Some paragraph text

- List item 1
- List item 2
`;

// Parse the document
const result = remark.parse(markdown);

// The document structure appears incomplete or malformed
```

### Expected behavior

The markdown parser should properly close all flow containers and finalize the document structure, ensuring all content is correctly parsed and represented in the AST.

### System Info
- remark version: 15.0.1
- Node version: 18.x

---
Repository: /testbed
