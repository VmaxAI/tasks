# Bug Report

### Describe the bug

I'm experiencing an issue with DOM node insertion where elements are being placed in the wrong position when moving nodes within the DOM tree. When I try to reorder elements or move a node from one parent to another, the node ends up appearing after the intended anchor point instead of before it.

### Reproduction

```js
const container = document.createElement('div')
const child1 = document.createElement('span')
const child2 = document.createElement('span')
const child3 = document.createElement('span')

child1.textContent = '1'
child2.textContent = '2'
child3.textContent = '3'

container.appendChild(child1)
container.appendChild(child2)
container.appendChild(child3)

// Try to move child3 before child2
// Expected order: 1, 3, 2
// Actual order: 1, 2, 3 (or something else unexpected)
```

When using Vue's rendering system to reorder elements in a list or move components around, the nodes don't end up in the correct position relative to the anchor element.

### Expected behavior

When inserting a node with an anchor, the node should be inserted immediately before the anchor element, not after it. The standard DOM `insertBefore` behavior should be maintained.

### System Info
- Vue version: 3.x
- Browser: All browsers

---
Repository: /testbed
