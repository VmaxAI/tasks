# Bug Report

### Describe the bug

I'm experiencing an issue with paragraph parsing in markdown content. When processing markdown text with paragraphs, the parser appears to be handling the paragraph structure incorrectly, causing unexpected behavior in the output.

### Reproduction

```js
const markdown = `This is a paragraph.

This is another paragraph.`;

// Process the markdown
const result = remark().parse(markdown);
```

When parsing simple paragraph content, the structure seems to be malformed. The paragraph tokens are not being created properly, which affects downstream processing.

### Expected behavior

Paragraphs should be properly entered and exited in the token stream, creating valid AST nodes that can be processed correctly by subsequent transformers.

### System Info
- remark version: 15.0.1
- Node version: 18.x

---
Repository: /testbed
