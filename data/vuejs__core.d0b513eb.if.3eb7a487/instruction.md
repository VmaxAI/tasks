# Bug Report

### Describe the bug

I'm encountering an issue where `withDirectives` throws an error when called outside of a render function, even though it should just return the vnode unchanged in that case. The function is now attempting to process directives when `currentRenderingInstance` is null, which leads to runtime errors.

### Reproduction

```js
import { h, withDirectives } from 'vue'

// Trying to use withDirectives outside render context
const vnode = h('div', 'Hello')
const result = withDirectives(vnode, [
  [someDirective, value]
])

// This throws an error instead of returning the vnode
```

### Expected behavior

When `withDirectives` is called outside of a render function (when `currentRenderingInstance` is null), it should:
1. Show a warning in dev mode
2. Return the vnode unchanged without attempting to process directives

The function should not try to access `currentRenderingInstance` or process directive bindings when there's no rendering context available.

### System Info
- Vue version: 3.x

---
Repository: /testbed
