# Bug Report

### Describe the bug

The `replaceReducer` function is not working at all after a recent update. When I try to dynamically replace the reducer in my store, it doesn't throw any errors but the new reducer doesn't seem to take effect. The store just stops responding to dispatched actions.

### Reproduction

```js
import { createStore } from 'redux'

const initialReducer = (state = { count: 0 }, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 }
    default:
      return state
  }
}

const store = createStore(initialReducer)

// Try to replace the reducer
const newReducer = (state = { count: 0 }, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 2 }
    default:
      return state
  }
}

store.replaceReducer(newReducer)

// Dispatch an action
store.dispatch({ type: 'INCREMENT' })

// The state doesn't update as expected
console.log(store.getState()) // Expected { count: 2 }, but behavior is broken
```

### Expected behavior

After calling `replaceReducer`, the store should use the new reducer for all subsequent dispatched actions. The validation that checks if the reducer is a function should also still work and throw an error if I pass something invalid like a string or number.

### System Info
- Redux version: latest
- Node: v18.x

---
Repository: /testbed
