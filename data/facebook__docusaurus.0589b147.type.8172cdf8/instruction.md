# Bug Report

### Describe the bug

I'm experiencing an issue with node type checking in the remark parser. When processing markdown AST nodes, the type validation is returning incorrect results and allowing invalid nodes to pass through.

### Reproduction

```js
const processor = remark();
const ast = processor.parse('# Hello');

// Type checking behaves unexpectedly
// Nodes with incorrect types are being accepted
// or valid nodes are being rejected incorrectly
```

When traversing the AST and checking node types, the validation logic seems to be broken. It's either accepting nodes that shouldn't match or rejecting valid nodes.

### Expected behavior

Node type checking should correctly validate that:
1. The node exists (is not null/undefined)
2. The node has the expected type property
3. Only nodes with the exact matching type pass the check

### System Info
- remark version: 15.0.1
- Node.js version: 18.x

---
Repository: /testbed
