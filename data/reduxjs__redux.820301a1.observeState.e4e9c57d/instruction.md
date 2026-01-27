# Bug Report

### Describe the bug

The store subscription system appears to be completely broken. When subscribing to state changes using `store.subscribe()`, the observer callback is never invoked when the state updates. This makes it impossible to react to state changes in the application.

### Reproduction

```js
import { createStore } from 'redux'

const store = createStore((state = { count: 0 }, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 }
    default:
      return state
  }
})

// Subscribe to store changes
const unsubscribe = store.subscribe(() => {
  console.log('State changed:', store.getState())
})

// Dispatch an action
store.dispatch({ type: 'INCREMENT' })

// Expected: Console should log "State changed: { count: 1 }"
// Actual: Nothing is logged, the subscriber is never called
```

### Expected behavior

The subscriber callback should be invoked whenever the state changes after dispatching an action. The observer's `next()` method should be called with the updated state.

### System Info
- Redux version: Latest
- Node version: 18.x

This is blocking our entire application from functioning properly as we rely heavily on store subscriptions for updating the UI. Any help would be greatly appreciated!

---
Repository: /testbed
