# Bug Report

### Describe the bug

When accessing `vnode.data` in Vue 2 compatibility mode, it always returns `undefined` instead of the vnode's props. Additionally, setting `vnode.data` doesn't actually update the props - the assignment has no effect.

### Reproduction

```js
// In a component using legacy render function
render(h) {
  const vnode = h('div', { class: 'test', id: 'myDiv' })
  
  console.log(vnode.data) // Expected: { class: 'test', id: 'myDiv' }
                          // Actual: undefined
  
  vnode.data = { class: 'updated' }
  console.log(vnode.props) // Expected: { class: 'updated' }
                           // Actual: { class: 'test', id: 'myDiv' } (unchanged)
}
```

### Expected behavior

- `vnode.data` should return the vnode's props object (or an empty object if props is null/undefined)
- Setting `vnode.data` should update the vnode's props

This is breaking compatibility with Vue 2 code that relies on accessing or modifying `vnode.data` in render functions.

### System Info

- Vue version: 3.x (compat mode)
- Migration from Vue 2 codebase

---
Repository: /testbed
