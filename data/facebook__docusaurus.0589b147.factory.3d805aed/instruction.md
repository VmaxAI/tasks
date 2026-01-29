# Bug Report

### Describe the bug

The AST visitor is not completing tree traversal properly when visiting nodes. The visitor function seems to be cutting off early and not returning the complete result, which causes unexpected behavior when processing syntax trees.

### Reproduction

```js
const tree = {
  type: 'root',
  children: [
    {
      type: 'paragraph',
      children: [
        { type: 'text', value: 'hello' }
      ]
    }
  ]
};

// Visit all nodes in the tree
visitParents(tree, (node) => {
  console.log(node.type);
});

// Expected: logs 'root', 'paragraph', 'text'
// Actual: visitor doesn't complete properly
```

The tree traversal doesn't work as expected and seems to terminate prematurely. This affects any code that relies on walking through the entire AST structure.

### Expected behavior

The visitor should traverse the entire tree and properly return results for each node visited. All nodes in the tree should be processed according to the visitor function.

### System Info
- Node version: 18.x
- Using unist-util-remove-position vendor code

---
Repository: /testbed
