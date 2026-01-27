# Bug Report

### Describe the bug

I'm experiencing unexpected behavior with `store.subscribe()` when trying to add listeners outside of a reducer execution. The store is throwing an error when I attempt to subscribe to state changes in what should be a valid scenario.

### Reproduction

```js
import { createStore } from 'redux'

const reducer = (state = {}, action) => {
  return state
}

const store = createStore(reducer)

// This throws an error unexpectedly
store.subscribe(() => {
  console.log('State changed:', store.getState())
})
```

### Expected behavior

The subscription should be registered successfully when called outside of a reducer execution. According to the Redux documentation, `store.subscribe()` should only throw an error when called *during* a reducer execution, not when called normally in application code.

The error message I'm getting also seems contradictory - it says I can't subscribe while the reducer is executing, but I'm clearly not inside a reducer at this point.

### System Info
- Redux version: latest
- Node: 18.x

---
Repository: /testbed
