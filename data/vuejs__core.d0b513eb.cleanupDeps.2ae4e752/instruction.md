# Bug Report

### Describe the bug

I'm experiencing an issue with reactivity cleanup where effects are not properly tracking dependencies after they've been re-evaluated. It seems like the dependency list gets corrupted during the cleanup phase, causing some dependencies to be incorrectly removed or retained.

### Reproduction

```js
import { reactive, effect } from 'vue'

const state = reactive({
  show: true,
  a: 1,
  b: 2
})

effect(() => {
  if (state.show) {
    console.log(state.a)
  } else {
    console.log(state.b)
  }
})

// Toggle condition multiple times
state.show = false
state.show = true
state.show = false

// Now changing 'a' doesn't trigger the effect even though show is true
state.a = 10
```

After toggling the condition several times, the effect stops responding to changes in properties that should be tracked. The dependency tracking seems to get out of sync.

### Expected behavior

The effect should continue to properly track and respond to changes in `state.a` when `state.show` is true, and to `state.b` when `state.show` is false, regardless of how many times the condition is toggled.

### System Info
- Vue version: 3.x
- Node: 18.x

---
Repository: /testbed
