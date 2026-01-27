# Bug Report

### Describe the bug

When using the `h()` function with more than 3 arguments, the props object is being included in the children array instead of being treated as props. This causes the component to receive incorrect children and the props are not properly applied.

### Reproduction

```js
import { h } from 'vue'

// Using h() with multiple children as separate arguments
const vnode = h(
  'div',
  { class: 'container' },
  'First child',
  'Second child',
  'Third child'
)

// Expected: props = { class: 'container' }, children = ['First child', 'Second child', 'Third child']
// Actual: The props object gets included in the children array
```

### Expected behavior

When calling `h()` with multiple arguments (type, props, ...children), the second argument should be treated as props and all subsequent arguments should become the children array. The props object should not be included in the children.

### System Info
- Vue version: 3.x

This seems to be affecting any component that uses `h()` with multiple child arguments instead of passing children as an array.

---
Repository: /testbed
