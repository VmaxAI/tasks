# Bug Report

### Describe the bug

I'm experiencing an issue with `pauseTracking()` where the tracking state isn't being properly restored after pausing. When I pause tracking and then resume it, the reactivity system seems to be in the wrong state.

### Reproduction

```js
import { reactive, effect, pauseTracking, resetTracking } from '@vue/reactivity'

const state = reactive({ count: 0 })
let dummy

effect(() => {
  dummy = state.count
})

// Initial value
console.log(dummy) // 0

// Pause tracking
pauseTracking()
state.count++

// Resume tracking
resetTracking()
state.count++

console.log(dummy) // Expected: 2, but reactivity might not work as expected
```

The issue appears to be related to how the tracking stack is being managed. After calling `pauseTracking()`, subsequent calls to `resetTracking()` don't properly restore the previous tracking state.

### Expected behavior

When `pauseTracking()` is called, it should save the current tracking state to the stack and disable tracking. When `resetTracking()` is called, it should restore the previous state from the stack. The reactivity system should work correctly after resuming tracking.

### System Info
- Vue version: 3.x
- Environment: Node.js

---
Repository: /testbed
