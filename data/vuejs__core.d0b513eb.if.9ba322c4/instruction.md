# Bug Report

### Describe the bug

I'm getting a runtime error when trying to pass an already wrapped effect function to `effect()` again. The code crashes with a "Cannot read property 'fn' of undefined" error.

### Reproduction

```js
import { effect, reactive } from 'vue'

const state = reactive({ count: 0 })

// Create an effect
const runner = effect(() => {
  console.log(state.count)
})

// Try to wrap the same runner in another effect
const wrappedRunner = effect(runner)
```

When running this code, I get an error because the code is trying to access properties incorrectly on the effect runner.

### Expected behavior

The effect should either:
1. Unwrap the existing effect and use the original function, OR
2. Throw a clear error message indicating that wrapping an effect runner is not supported

Instead, it crashes with an unclear error about undefined properties.

### System Info
- Vue version: 3.x
- Node version: 18.x

---
Repository: /testbed
