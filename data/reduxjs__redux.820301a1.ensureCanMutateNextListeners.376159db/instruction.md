# Bug Report

### Describe the bug

I'm experiencing an issue where listeners added during a dispatch cycle are not being called correctly. It seems like the subscription mechanism is not properly handling concurrent modifications to the listener list.

### Reproduction

```js
const store = createStore(reducer, initialState)

store.dispatch({ type: 'INIT' })

// Subscribe during dispatch
store.subscribe(() => {
  console.log('Listener 1')
  
  // Subscribe another listener from within a listener
  store.subscribe(() => {
    console.log('Listener 2')
  })
})

store.dispatch({ type: 'UPDATE' })
// Expected: Both listeners should be called on subsequent dispatches
// Actual: Listener behavior is inconsistent
```

### Expected behavior

When subscribing to the store, even if subscriptions happen during a dispatch, all registered listeners should be called on the next dispatch. The store should maintain a proper snapshot of listeners to avoid race conditions.

### System Info
- Redux version: latest
- Node: 18.x

This seems related to how the listener list is being copied when mutations are needed. The current behavior makes it difficult to dynamically add listeners based on state changes.

---
Repository: /testbed
