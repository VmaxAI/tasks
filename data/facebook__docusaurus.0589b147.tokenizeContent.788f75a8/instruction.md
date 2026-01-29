# Bug Report

### Describe the bug

I'm encountering an issue with MDX content parsing where the tokenizer seems to get stuck in an infinite loop or doesn't properly continue processing content chunks. The parser appears to hang when processing certain MDX content with multiple content chunks.

### Reproduction

```js
const mdx = `
# Hello

This is some content.

More content here.
`;

// Parser hangs or doesn't process correctly
const result = compile(mdx);
```

### Expected behavior

The MDX content should be parsed successfully and all content chunks should be processed sequentially. The tokenizer should properly link content chunks together and continue processing until the end of the document.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
