# Bug Report

### Describe the bug
When subscribing to store state changes using the Observable pattern, the observer's `next` callback is not being invoked when the state updates. The subscription appears to be set up correctly, but state changes don't trigger the observer function.

### Reproduction
```js
const store = createStore(reducer, initialState)

const observer = {
  next: (state) => {
    console.log('State updated:', state)
  }
}

store.subscribe(observer)

// Dispatch an action that changes state
store.dispatch({ type: 'UPDATE' })

// Expected: observer.next should be called with new state
// Actual: observer.next is never invoked
```

### Expected behavior
The observer's `next` method should be called with the current state whenever the store state changes. The callback should receive the actual state object, not a function reference.

### System Info
- Redux version: latest
- Environment: Node.js

---
Repository: /testbed
