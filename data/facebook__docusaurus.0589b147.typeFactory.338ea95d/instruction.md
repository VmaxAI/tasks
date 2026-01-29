# Bug Report

### Describe the bug

I'm experiencing an issue with node type checking in the remark parser. It seems like nodes are being incorrectly identified or filtered - nodes that should match a specific type are being rejected, and nodes that shouldn't match are being accepted.

### Reproduction

```js
// When checking for a specific node type, the behavior is inverted
const checker = typeFactory('paragraph')

// This returns true when the node is NOT a paragraph
checker({ type: 'heading' }) // returns true (unexpected)

// This returns false when the node IS a paragraph  
checker({ type: 'paragraph' }) // returns false (unexpected)
```

The type checking logic appears to be backwards - it's accepting nodes that don't match the specified type and rejecting nodes that do match.

### Expected behavior

When using `typeFactory` with a specific node type, it should:
- Return `true` for nodes matching that type
- Return `false` for nodes not matching that type

### System Info
- remark version: 15.0.1
- Node version: 18.x

This is causing issues with AST traversal and node filtering in my markdown processing pipeline. Any nodes I try to filter by type end up giving me the opposite set of nodes than what I need.

---
Repository: /testbed
