# Bug Report

### Describe the bug
When subscribing to store state changes using `subscribe()`, the observer's `next` callback is being called without the current state as an argument. The subscription is triggered but the state value is not being passed to the observer function.

### Reproduction
```js
const store = createStore(/* ... */)

store.subscribe({
  next: (state) => {
    console.log('Current state:', state)
    // state is undefined instead of the actual state object
  }
})

// Dispatch an action to trigger the observer
store.dispatch({ type: 'SOME_ACTION' })
```

### Expected behavior
The observer's `next` function should receive the current state as its first argument whenever the store updates. This is how Redux observables are supposed to work - subscribers should get the updated state passed to them so they can react to the changes.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
