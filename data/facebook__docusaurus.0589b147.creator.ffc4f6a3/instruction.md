# Bug Report

### Describe the bug

I'm experiencing an issue with the MDX parser where tokenization seems to be broken. After recent changes, the parser appears to be returning a function instead of actually executing the tokenizer, which causes parsing to fail silently or produce incorrect results.

### Reproduction

```js
const mdx = require('@mdx-js/mdx');

const content = `
# Hello World

This is a test MDX document.
`;

// Try to parse MDX content
const result = mdx.compile(content);
// Parser doesn't work as expected
```

### Expected behavior

The MDX content should be parsed correctly and the tokenizer should execute properly during the parsing process. The parser should process the content and return the expected output.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: Latest

This seems to have started happening recently. The parser was working fine before but now it's not processing content correctly.

---
Repository: /testbed
