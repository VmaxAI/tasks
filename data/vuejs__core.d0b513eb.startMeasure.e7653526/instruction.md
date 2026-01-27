# Bug Report

### Describe the bug

The performance measurement timestamps in devtools are showing incorrect values. When performance API is not supported by the browser, the devtools profiling data displays wrong timing information, making it impossible to accurately measure component render times.

### Reproduction

```js
// In a browser that doesn't support performance.mark/measure
const app = createApp({
  setup() {
    // Component with some rendering logic
    return () => h('div', 'Hello')
  }
})

app.config.performance = true
app.mount('#app')

// Check devtools profiling data - timestamps will be incorrect
```

### Expected behavior

When the performance API is not available, devtools should fall back to `Date.now()` for accurate timestamps. Currently it seems to be using the wrong timing source based on the support check.

### System Info
- Vue version: 3.x
- Browser: Safari (or any browser without full performance API support)
- Devtools: Latest version

The issue affects profiling accuracy when trying to debug performance issues in environments with limited performance API support.

---
Repository: /testbed
