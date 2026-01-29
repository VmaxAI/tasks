# Bug Report

### Describe the bug

When using the `inject` option with an array syntax in component options, the injections are not being resolved correctly. The component fails to receive the injected values from parent components.

### Reproduction

```js
// Parent component
export default {
  provide: {
    message: 'Hello from parent'
  }
}

// Child component
export default {
  inject: ['message'],
  mounted() {
    console.log(this.message) // undefined or error
  }
}
```

### Expected behavior

The child component should be able to access the injected `message` property with the value `'Hello from parent'`. The array syntax for `inject` should work as documented.

### System Info
- Vue version: 3.x

---
Repository: /testbed
