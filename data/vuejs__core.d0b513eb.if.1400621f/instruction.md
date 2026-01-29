# Bug Report

### Describe the bug

When trying to register the same mixin multiple times on an app instance, the mixin gets added to the app every time instead of being rejected after the first registration. This causes the mixin's logic to be executed multiple times, leading to duplicate behavior and potential performance issues.

### Reproduction

```js
import { createApp } from 'vue'

const myMixin = {
  name: 'MyMixin',
  created() {
    console.log('Mixin created hook called')
  }
}

const app = createApp({})

// Register the same mixin twice
app.mixin(myMixin)
app.mixin(myMixin)

app.mount('#app')

// Expected: "Mixin created hook called" logged once
// Actual: "Mixin created hook called" logged twice
```

### Expected behavior

The mixin should only be registered once. Subsequent attempts to register the same mixin should be ignored (with a warning in dev mode), but the mixin should not be added multiple times to the app's mixins array.

### System Info

- Vue version: 3.x
- Build: with Options API support enabled

---
Repository: /testbed
