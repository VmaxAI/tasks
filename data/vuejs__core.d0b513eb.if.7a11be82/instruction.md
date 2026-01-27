# Bug Report

### Describe the bug

I'm encountering an issue when trying to pass an effect runner back to the `effect()` function. The unwrapping logic seems to be broken and instead of extracting the original function, it's extracting something else entirely.

### Reproduction

```js
import { effect } from '@vue/reactivity'

const runner = effect(() => {
  console.log('effect running')
})

// Try to create a new effect from the existing runner
const newRunner = effect(runner)

// This throws an error or behaves unexpectedly
newRunner()
```

### Expected behavior

When passing an effect runner to `effect()`, it should properly unwrap the original function and create a new effect with it. The new runner should execute the same logic as the original.

### System Info
- Vue reactivity version: latest
- Node.js version: 18.x

---
Repository: /testbed
