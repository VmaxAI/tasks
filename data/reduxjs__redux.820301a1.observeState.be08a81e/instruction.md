# Bug Report

### Describe the bug

When subscribing to store state changes, the observer's `next` callback is being invoked without the current state as an argument. This breaks the expected behavior where observers should receive the state value when notified of changes.

### Reproduction

```js
const store = createStore(reducer, initialState)

store.subscribe({
  next: (state) => {
    console.log('Current state:', state)
    // state is undefined instead of the actual state object
  }
})

// Dispatch an action
store.dispatch(someAction)
```

### Expected behavior

The `next` callback should receive the current state as its argument, allowing observers to access the updated state value. Instead, `undefined` is being passed to the callback.

### System Info
- Redux version: latest
- Environment: Node.js

---
Repository: /testbed
