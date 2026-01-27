# Bug Report

### Describe the bug

The `$watch` API is not working correctly when the Options API feature flag is enabled. It seems like the function is not being bound to the component instance properly, causing issues when trying to watch reactive properties.

### Reproduction

```js
export default {
  data() {
    return {
      count: 0
    }
  },
  mounted() {
    // This doesn't work as expected
    this.$watch('count', (newVal, oldVal) => {
      console.log('Count changed:', newVal, oldVal)
    })
    
    this.count = 1 // Watcher callback is not triggered
  }
}
```

### Expected behavior

The watcher callback should be invoked when the watched property changes. The `$watch` method should work correctly when called on the component instance.

### System Info
- Vue version: 3.x
- Build: with Options API enabled

---
Repository: /testbed
