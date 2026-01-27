# Bug Report

### Describe the bug

When applying the same mixin multiple times to an app instance, the mixin gets added to the app context on every subsequent application instead of being rejected. This causes the mixin to be applied multiple times, leading to duplicate lifecycle hooks, computed properties, and methods being registered.

### Reproduction

```js
import { createApp } from 'vue'

const myMixin = {
  name: 'TestMixin',
  created() {
    console.log('Mixin created hook called')
  }
}

const app = createApp({})

// Apply the same mixin twice
app.mixin(myMixin)
app.mixin(myMixin)  // Should warn but currently adds it again

app.mount('#app')
// Expected: "Mixin created hook called" logged once
// Actual: "Mixin created hook called" logged twice
```

### Expected behavior

The mixin should only be applied once. When attempting to apply the same mixin again, it should be ignored and a warning should be shown in development mode (if the warning is enabled).

### System Info

- Vue version: 3.x
- Build: with Options API support enabled

---
Repository: /testbed
