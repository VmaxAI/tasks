# Bug Report

### Describe the bug

The store creation is broken when passing a function as the `preloadedState` parameter without an explicit `enhancer` argument. It seems like the automatic detection/swapping of these parameters is no longer working.

### Reproduction

```js
import { createStore } from 'redux'

const reducer = (state = {}, action) => state

// This should work - passing enhancer as second argument
const store = createStore(reducer, someEnhancer)
```

When you try to create a store this way, it fails to properly recognize that the second argument is an enhancer function and should be treated as such.

### Expected behavior

When `preloadedState` is a function and `enhancer` is undefined, the library should automatically swap them - treating the function as an enhancer instead of preloadedState. This is the documented behavior for backwards compatibility.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
