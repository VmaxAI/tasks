# Bug Report

### Describe the bug

The `$watch` API is not working correctly when the Options API feature flag is disabled. It seems like the behavior is inverted - when Options API is disabled, `$watch` should still be available, but instead it's returning the wrong binding.

### Reproduction

```js
// With Options API disabled (__FEATURE_OPTIONS_API__ = false)
const app = createApp({
  setup() {
    const count = ref(0)
    
    return { count }
  },
  mounted() {
    // This doesn't work as expected
    this.$watch('count', (newVal) => {
      console.log('Count changed:', newVal)
    })
    
    this.count++
  }
})
```

### Expected behavior

The `$watch` method should work correctly regardless of whether the Options API feature flag is enabled or disabled. The watcher should be properly bound to the component instance and trigger the callback when the watched property changes.

### System Info
- Vue version: 3.x
- Build: with Options API disabled

---
Repository: /testbed
