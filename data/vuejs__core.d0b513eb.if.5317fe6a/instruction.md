# Bug Report

### Describe the bug

After a recent update, reactive effects are not being triggered at all. Components that should re-render when reactive state changes are completely frozen and don't update anymore.

### Reproduction

```js
import { reactive, effect } from 'vue'

const state = reactive({ count: 0 })

effect(() => {
  console.log('Count:', state.count)
})

// This should trigger the effect but nothing happens
state.count = 1
state.count = 2
```

Expected to see console logs for each update, but the effect only runs once during initialization and never again.

### Steps to reproduce
1. Create a reactive object
2. Set up an effect that depends on a property
3. Modify the property
4. The effect doesn't run

This is blocking our entire application from working. Any reactive state changes are completely ignored and the UI is stuck in its initial state.

### System Info
- Vue version: 3.x
- Node version: 18.x

---
Repository: /testbed
