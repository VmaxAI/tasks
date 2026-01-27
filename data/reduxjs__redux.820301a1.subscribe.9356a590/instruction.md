# Bug Report

### Describe the bug

I'm having an issue with the `subscribe` method on the store. When I try to subscribe an observer to state changes, nothing happens - the observer's `next` callback never gets called even though the state is updating.

### Reproduction

```js
const store = createStore(reducer, initialState)

const observer = {
  next: (state) => {
    console.log('State changed:', state)
  }
}

store.subscribe(observer)

// Dispatch some actions
store.dispatch({ type: 'UPDATE_VALUE' })

// Expected: observer.next should be called
// Actual: Nothing happens, no console output
```

### Expected behavior

The observer's `next` method should be called whenever the state changes. The initial state should also be passed to the observer immediately upon subscription.

### Additional context

This was working fine before, but after a recent update the subscription seems to be broken. The subscribe method accepts the observer without throwing any errors, but the callback is never invoked.

---
Repository: /testbed
