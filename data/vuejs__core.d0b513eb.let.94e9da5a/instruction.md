# Bug Report

### Describe the bug

I'm experiencing an issue where inserting nodes at specific positions in the DOM is failing unexpectedly. When trying to insert a child node before a reference node that happens to be the first child (at index 0), the operation throws an error claiming the reference node is not a child of the parent, even though it actually is.

### Reproduction

```js
const parent = document.createElement('div')
const firstChild = document.createElement('span')
const newChild = document.createElement('p')

// Add first child to parent
parent.appendChild(firstChild)

// Try to insert new child before the first child (at index 0)
parent.insertBefore(newChild, firstChild)
// Error: ref is not a child of parent
```

### Expected behavior

The insertion should succeed when the reference node is at index 0. The new child should be inserted before the first child without throwing an error.

### System Info
- Vue version: 3.x
- Runtime: test environment

This seems to be a regression as this was working fine before. The error message is misleading since the reference node IS actually a child of the parent.

---
Repository: /testbed
