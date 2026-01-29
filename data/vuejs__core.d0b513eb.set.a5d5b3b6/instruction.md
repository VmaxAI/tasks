# Bug Report

### Describe the bug

I'm experiencing an issue with VNode properties in compatibility mode. When accessing the `data` property on a VNode, it always returns an empty object `{}` instead of the actual props, even when `vnode.props` contains data.

### Reproduction

```js
const vnode = {
  type: 'div',
  props: {
    class: 'test',
    id: 'my-id'
  }
}

// In compatibility mode, accessing vnode.data
console.log(vnode.data) // Expected: { class: 'test', id: 'my-id' }
                        // Actual: {}
```

### Expected behavior

The `data` property should return the actual props object when it exists, not an empty object. This is breaking compatibility with Vue 2 code that relies on reading VNode data.

### System Info
- Vue version: 3.x (compat mode)
- Migrating from Vue 2.x

---
Repository: /testbed
