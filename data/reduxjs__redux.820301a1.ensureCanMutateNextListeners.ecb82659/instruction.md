# Bug Report

### Describe the bug

I'm experiencing an issue with store subscriptions where listeners are not being called properly after subscribing and dispatching actions. It seems like the subscription mechanism is broken - sometimes listeners fire multiple times, other times they don't fire at all.

### Reproduction

```js
const store = createStore(reducer, initialState)

// Subscribe to store changes
const unsubscribe = store.subscribe(() => {
  console.log('State changed:', store.getState())
})

// Dispatch an action
store.dispatch({ type: 'UPDATE_VALUE', payload: 'new value' })

// Expected: listener should be called once
// Actual: listener behavior is inconsistent
```

### Steps to reproduce:
1. Create a store with a simple reducer
2. Add a subscription listener
3. Dispatch multiple actions
4. Observer that listeners don't get called consistently or get called with wrong timing

This is causing major issues in my application where components aren't updating when the store changes. The problem seems to have appeared recently, possibly after some internal refactoring of the subscription system.

### Expected behavior

Subscriptions should reliably fire whenever an action is dispatched and the state changes. Each listener should be called exactly once per dispatch.

### System Info
- Redux version: latest
- Node: v18.x

---
Repository: /testbed
