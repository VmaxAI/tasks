# Bug Report

### Describe the bug

The markdown parser appears to hang indefinitely when processing certain input. The application becomes unresponsive and never completes the parsing operation.

### Reproduction

```js
const remark = require('remark');

// This causes the parser to hang
const processor = remark();
const result = processor.processSync('# Hello World');
// Never completes...
```

I've noticed this happens with any markdown input. The parser seems to get stuck in an infinite loop during the postprocessing phase and never returns.

### Expected behavior

The parser should complete processing and return the parsed markdown AST without hanging.

### System Info
- remark version: 15.0.1
- Node version: 18.x

---
Repository: /testbed
