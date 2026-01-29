# Bug Report

### Describe the bug

I'm experiencing an issue with the AST visitor function where traversal seems to break or behave unexpectedly. When processing nested nodes in a syntax tree, the visitor appears to stop prematurely or return incorrect results.

### Reproduction

```js
const tree = {
  type: 'root',
  children: [
    {
      type: 'parent',
      children: [
        { type: 'leaf', value: 'test1' },
        { type: 'leaf', value: 'test2' }
      ]
    }
  ]
};

// Visit all nodes
visitParents(tree, (node) => {
  console.log(node.type);
  // Expected to visit all nodes but doesn't complete properly
});
```

### Expected behavior

The visitor should traverse through all nodes in the tree correctly and complete the full traversal without issues. All child nodes should be visited in the expected order.

### System Info
- Node version: 18.x
- Browser: N/A (server-side)

This seems to have started happening recently. The tree traversal worked fine before but now it's cutting off early or not returning the right values.

---
Repository: /testbed
