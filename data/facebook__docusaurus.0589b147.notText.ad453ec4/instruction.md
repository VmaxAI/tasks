# Bug Report

### Describe the bug

I'm experiencing an issue with text parsing where the parser seems to be entering the wrong token type. When parsing content, it appears that text nodes are being incorrectly labeled, which is causing downstream issues with the AST structure.

### Reproduction

```js
// Parse markdown content with text
const result = remark.parse('Some regular text content')

// The AST shows incorrect token types for text nodes
console.log(result)
```

When I inspect the generated AST, text content that should be properly categorized is showing up with the wrong type identifier. This affects any processing that relies on the correct token structure.

### Expected behavior

Text nodes in the parsed AST should have the correct type identifier so that subsequent processing steps can properly handle the content.

### System Info
- remark version: 15.0.1
- Node version: 18.x

---
Repository: /testbed
