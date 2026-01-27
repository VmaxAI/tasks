# Bug Report

### Describe the bug

I'm experiencing an issue with node removal operations where the operation logging seems to be inverted. When removing nodes from the DOM, the logged operations don't match what's actually happening - it appears that the logging behavior is backwards from what it should be.

### Reproduction

```js
const parent = createNode('div')
const child = createNode('span')
parent.children.push(child)
child.parentNode = parent

// Remove the child node
remove(child, true)

// Check the logged operations
// Expected: Should log a REMOVE operation
// Actual: No REMOVE operation is logged, or wrong operation type is logged
```

### Expected behavior

When `remove()` is called with `logOp = true`, it should log a REMOVE operation. When called with `logOp = false`, it should skip logging entirely. The logging should correctly reflect the actual operation being performed (removal of a node).

### System Info
- Vue version: 3.x
- Runtime: test environment

---
Repository: /testbed
