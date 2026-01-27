# Bug Report

### Describe the bug

I'm experiencing an issue with the `$destroy` method in Vue 3 compatibility mode. When I try to call `$destroy()` on a component instance, it doesn't actually destroy the component anymore. The method seems to be a no-op regardless of whether the compat destroy function exists or not.

### Reproduction

```js
import { createApp } from 'vue'

const app = createApp({
  template: '<div>Test</div>',
  mounted() {
    console.log('Component mounted')
  },
  beforeUnmount() {
    console.log('Component being destroyed')
  }
})

const vm = app.mount('#app')

// This should destroy the component but does nothing
vm.$destroy()
// Expected: "Component being destroyed" should be logged
// Actual: Nothing happens
```

### Expected behavior

When calling `$destroy()` on a component instance in compatibility mode, the component should be properly destroyed and lifecycle hooks like `beforeUnmount` should be triggered.

### System Info
- Vue version: 3.x (compat mode enabled)
- Node version: 18.x

This seems like a regression as `$destroy` was working in previous versions when using the compat build.

---
Repository: /testbed
