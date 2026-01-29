# Bug Report

### Describe the bug

I'm experiencing an issue with SSR compilation where nested data structures are not being properly isolated. When I have components with nested objects or arrays in their props/data, modifications to one instance seem to affect other instances.

### Reproduction

```js
// Component with nested prop structure
const component = {
  props: {
    config: {
      type: Object,
      default: () => ({
        options: ['a', 'b', 'c'],
        settings: {
          enabled: true
        }
      })
    }
  }
}

// When rendering multiple instances in SSR:
// Instance 1 modifies config.options
instance1.config.options.push('d')

// Instance 2 unexpectedly sees the modification
// instance2.config.options now also contains 'd'
```

### Expected behavior

Each component instance should have its own isolated copy of nested data structures. Changes to arrays or nested objects in one instance should not affect other instances during SSR rendering.

### System Info
- Vue version: 3.x
- SSR compilation context

This seems to be related to how the SSR compiler handles cloning of nested structures. The data appears to be shared between instances rather than being properly deep-cloned.

---
Repository: /testbed
