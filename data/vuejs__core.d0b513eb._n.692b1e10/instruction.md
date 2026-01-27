# Bug Report

### Describe the bug

I'm experiencing an issue with the `_n` helper function in the compatibility layer. It appears that the function is not being properly assigned, which is causing problems when using legacy Vue 2 template compilation features.

### Reproduction

When using Vue 3's compatibility mode with Vue 2 templates that rely on the `_n` helper (used for converting values to numbers in templates), the application throws an error or behaves unexpectedly.

```js
// In a Vue 2 style template that gets compiled:
// <input v-model.number="value">

// The compiled render function tries to call _n() but it's not properly defined
// This causes runtime errors when the template is rendered
```

### Expected behavior

The `_n` helper should be available and properly convert values to numbers in compatibility mode, just like it did in Vue 2. Templates using `v-model.number` or other directives that rely on number conversion should work without errors.

### System Info
- Vue version: 3.x (compatibility mode)
- Using legacy template compilation

---
Repository: /testbed
