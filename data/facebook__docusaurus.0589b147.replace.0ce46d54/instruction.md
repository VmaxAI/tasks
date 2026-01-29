# Bug Report

### Describe the bug

The `replace()` function in the AST walker is not working correctly. When trying to replace a node with a new node, nothing happens and the original node remains in the tree.

### Reproduction

```js
const walker = new SyncWalker(ast, {
  enter(node, parent, key, index) {
    if (node.type === 'Paragraph') {
      // Try to replace the paragraph with a heading
      this.replace({
        type: 'Heading',
        depth: 1,
        children: node.children
      });
    }
  }
});

walker.visit(ast);
// The paragraph node is still there, replacement didn't work
```

### Expected behavior

When calling `this.replace()` with a new node object, the current node should be replaced with the provided node in the AST. The walker should continue processing with the replacement node.

### Additional context

This seems to have broken recently. The `replace()` method just doesn't do anything anymore - the tree stays unchanged after calling it.

---
Repository: /testbed
