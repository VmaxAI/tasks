# Bug Report

### Describe the bug

I'm experiencing an issue with markdown link parsing where the URL is being assigned to the wrong node in the AST. When parsing markdown with resource links (like `[text](url)`), the URL destination seems to be getting attached to an incorrect node in the stack, causing the link structure to be malformed.

### Reproduction

```js
// Parse markdown with a link
const markdown = '[Example Link](https://example.com)'

// After parsing, the URL is not attached to the correct link node
// The link node doesn't have the expected `url` property set correctly
```

### Expected behavior

The URL from a markdown link should be properly attached to the corresponding link node in the AST. When parsing `[text](url)`, the resulting link node should have its `url` property set to the correct destination value.

### System Info
- remark version: 15.0.1

---
Repository: /testbed
