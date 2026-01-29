# Bug Report

### Describe the bug

I'm experiencing an issue with the markdown parser where tokenization appears to be broken. When parsing markdown content, the tokenizer seems to be receiving incorrect arguments, causing parsing to fail or produce unexpected results.

### Reproduction

```js
const remark = require('remark');

const markdown = `
# Hello World

This is a test paragraph.
`;

const result = remark.parse(markdown);
console.log(result);
```

When running this code, the parser doesn't work as expected. The tokenizer appears to be receiving the wrong parameters internally.

### Expected behavior

The markdown should be parsed correctly and return a proper AST structure with the heading and paragraph nodes.

### System Info
- remark version: 15.0.1
- Node version: Latest

---
Repository: /testbed
