# Bug Report

### Describe the bug

I'm experiencing an issue with the markdown parser where it crashes with a `TypeError` when processing certain markdown content. The error occurs when trying to access properties on `undefined` during tokenization.

### Reproduction

```js
const remark = require('remark');

const markdown = `
# Test heading

Some content here with **bold text**.

- List item 1
- List item 2
`;

// This causes a crash
remark.parse(markdown);
```

The parser throws an error like `Cannot read property 'from' of undefined` when processing the markdown.

### Expected behavior

The markdown should be parsed successfully without throwing errors. The parser should handle cases where the `info` object might not be defined.

### System Info
- remark version: 15.0.1
- Node version: 18.x

---
Repository: /testbed
