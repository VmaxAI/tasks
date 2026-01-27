# Bug Report

### Describe the bug

I'm encountering an issue with the `clear()` method on reactive Map and Set objects. When calling `clear()` on an empty reactive collection, it seems to trigger reactivity updates even though no actual changes occurred. This causes unnecessary re-renders in my components.

### Reproduction

```js
import { reactive, effect } from 'vue'

const map = reactive(new Map())
let effectCount = 0

effect(() => {
  // Access the map to track it
  map.size
  effectCount++
})

// Clear an already empty map
map.clear()

// effectCount is now 2, but should be 1 since nothing changed
console.log(effectCount) // Expected: 1, Actual: 2
```

The same issue occurs with reactive Sets:

```js
const set = reactive(new Set())
let renderCount = 0

effect(() => {
  set.size
  renderCount++
})

set.clear() // Triggers effect even though set was already empty
```

### Expected behavior

Calling `clear()` on an empty reactive Map or Set should not trigger reactivity updates since no actual state change has occurred. The effect/component should only re-run when there are actual modifications to the collection.

### System Info
- Vue version: 3.x
- Environment: Node.js

This is causing performance issues in my app where I have collections that get cleared frequently, even when they're already empty. Any help would be appreciated!

---
Repository: /testbed
