# Bug Report

### Describe the bug
After a recent update, the store's observable functionality appears to be completely broken. When subscribing to state changes, observers are no longer being notified when the state updates.

### Reproduction
```js
const store = createStore(reducer, initialState)

const unsubscribe = store.subscribe(() => {
  console.log('State changed:', store.getState())
})

// Dispatch an action
store.dispatch({ type: 'UPDATE_VALUE', payload: 'new value' })

// Expected: Console log showing the updated state
// Actual: Nothing happens, observer is never called
```

### Expected behavior
The observer callback should be invoked whenever the state changes, allowing subscribers to react to state updates. This is core functionality for any store implementation and was working fine before.

### Additional context
This is breaking our entire application since none of our components are receiving state updates anymore. The store seems to accept dispatches but subscribers are never notified.

---
Repository: /testbed
