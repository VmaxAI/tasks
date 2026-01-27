# Bug Report

### Describe the bug

I'm experiencing an issue where the scheduler appears to be stuck in an infinite loop when flushing pre-flush callbacks in development mode. The application becomes unresponsive and eventually crashes with a "Maximum call stack size exceeded" error.

This seems to happen specifically when there are multiple pre-flush callbacks that trigger each other, which used to work fine in previous versions.

### Reproduction

```js
import { watchEffect, ref } from 'vue'

const count = ref(0)
const derived = ref(0)

// First watcher
watchEffect(() => {
  derived.value = count.value * 2
}, { flush: 'pre' })

// Second watcher that depends on the first
watchEffect(() => {
  console.log('Derived:', derived.value)
  if (derived.value < 10) {
    count.value++
  }
}, { flush: 'pre' })

count.value = 1
```

### Expected behavior

The watchers should execute normally without causing an infinite loop. The circular dependency detection should prevent the infinite recursion.

### System Info

- Vue version: 3.x (development build)
- Node version: 18.x
- OS: macOS

The issue only occurs in development mode, production builds seem unaffected.

---
Repository: /testbed
