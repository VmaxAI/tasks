# Bug Report

### Describe the bug

When using the compat build with Vue 3, legacy render functions that don't pass any props are now receiving an empty object `{}` instead of `null`. This breaks components that explicitly check for the absence of props using falsy checks.

### Reproduction

```js
// Legacy Vue 2 style render function
render(h) {
  // Component without props
  const vnode = h('div')
  
  // Previously: vnode.props would be null/undefined
  // Now: vnode.props is an empty object {}
  
  if (vnode.props) {
    // This block now incorrectly executes even when no props were passed
    console.log('Has props')
  }
}
```

### Expected behavior

When no props are passed to a legacy render function, the props should be `null` or `undefined`, not an empty object. This maintains backward compatibility with Vue 2 behavior where components could check for the presence of props using truthiness checks.

### System Info
- Vue version: 3.x (compat build)
- Using legacy render functions from Vue 2

---
Repository: /testbed
