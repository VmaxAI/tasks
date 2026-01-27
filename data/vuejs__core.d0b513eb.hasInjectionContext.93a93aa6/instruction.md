# Bug Report

### Describe the bug

I'm having an issue with `hasInjectionContext()` returning incorrect values. It seems like the function is being too strict and returning `false` even when there's a valid injection context available.

### Reproduction

```js
import { createApp, inject, hasInjectionContext } from 'vue'

const app = createApp({
  setup() {
    // This should return true since we're inside a component setup
    console.log(hasInjectionContext()) // returns false unexpectedly
    
    const injectedValue = inject('myKey', 'default')
    return {}
  }
})

app.provide('myKey', 'test value')
app.mount('#app')
```

In my case, I'm checking if injection context exists before calling `inject()`, but `hasInjectionContext()` is returning `false` even though I'm clearly inside a valid component setup function where injection should work.

### Expected behavior

`hasInjectionContext()` should return `true` when called from within a component's setup function or during rendering, since that's a valid context for using `inject()`.

### System Info
- Vue version: 3.x

---
Repository: /testbed
