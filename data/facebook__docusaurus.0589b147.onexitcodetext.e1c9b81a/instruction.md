# Bug Report

### Describe the bug

I'm experiencing an issue with inline code rendering in markdown parsing. When I have inline code that contains text, the parsed output seems to be missing or incorrectly structured.

### Reproduction

```js
const markdown = 'Some text with `inline code` in it'

// After parsing, the inline code node doesn't have the expected value
// or it's attached to the wrong parent node
```

When I parse markdown containing inline code blocks (backtick-wrapped text), the resulting AST doesn't correctly capture the code content. The value appears to be empty or not properly associated with the code node.

### Expected behavior

The inline code node should contain the text between the backticks as its value property. For example, parsing `` `hello` `` should create a code node with `value: 'hello'`.

### System Info
- remark version: 15.0.1
- Node version: Latest

This seems to have started happening recently. Previously inline code was working fine but now it's not capturing the content properly.

---
Repository: /testbed
