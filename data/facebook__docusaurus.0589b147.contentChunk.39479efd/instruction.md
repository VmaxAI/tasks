# Bug Report

### Describe the bug

I'm encountering an issue with fenced code blocks in MDX. When parsing code blocks, the content inside the block is not being properly captured. It seems like the parser is consuming characters but then immediately returning to the wrong state, causing the code block content to be lost or incorrectly processed.

### Reproduction

```mdx
```js
const example = 'test';
console.log(example);
```
```

When this MDX is parsed, the code block content doesn't render correctly. The code inside the fenced block appears to be skipped or malformed in the output.

### Expected behavior

The parser should correctly tokenize and capture all content within fenced code blocks, preserving the code exactly as written between the fence markers.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: Latest

This appears to have started happening recently. The code block parsing logic seems to have changed in how it handles the content chunks.

---
Repository: /testbed
