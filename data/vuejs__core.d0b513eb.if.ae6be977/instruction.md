# Bug Report

### Describe the bug

I'm experiencing an issue where reactive effects are not triggering properly. When I update a reactive value, the computed properties and watchers that depend on it don't seem to re-evaluate consistently. Sometimes the updates work, but other times they're completely ignored.

### Reproduction

```js
import { reactive, effect } from 'vue'

const state = reactive({ count: 0 })
let runCount = 0

effect(() => {
  console.log('Effect running, count:', state.count)
  runCount++
})

// Update the reactive state
state.count++
state.count++

// Expected runCount to be 3 (initial + 2 updates)
// But the effect doesn't always trigger
```

### Expected behavior

The effect should run every time `state.count` is modified. Each change to a reactive property should trigger all dependent effects to re-run.

### System Info
- Vue version: 3.x
- Node: 18.x

This seems to have started recently, possibly after a recent update. The reactivity system appears to be skipping some notifications.

---
Repository: /testbed
