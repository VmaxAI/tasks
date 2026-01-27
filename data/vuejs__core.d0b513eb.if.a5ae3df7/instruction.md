# Bug Report

### Describe the bug

When injecting refs using the `inject()` API, the injected value is not automatically unwrapped in the component context. Accessing the injected ref returns the ref object itself instead of its value.

### Reproduction

```js
// Parent component
provide('count', ref(0))

// Child component
export default {
  inject: ['count'],
  mounted() {
    console.log(this.count) // Expected: 0, Actual: Ref object
    console.log(this.count.value) // 0 - have to manually unwrap
  }
}
```

### Expected behavior

According to the Vue 3 documentation and previous behavior (ref #4196), injected refs should be automatically unwrapped when accessed through the component context, similar to how refs are unwrapped in templates. This means `this.count` should return the value directly, not the ref object.

### System Info
- Vue version: 3.x
- Node: 18.x

---
Repository: /testbed
