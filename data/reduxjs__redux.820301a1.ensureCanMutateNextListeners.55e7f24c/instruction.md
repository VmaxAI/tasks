# Bug Report

### Describe the bug

I'm experiencing an issue where store listeners are not being called after subscribing/unsubscribing during a dispatch cycle. It seems like the listener management is broken and callbacks that should be invoked are being skipped.

### Reproduction

```js
const store = createStore(reducer, initialState)

store.dispatch({ type: 'START' })

const unsubscribe = store.subscribe(() => {
  console.log('Listener called')
})

store.dispatch({ type: 'UPDATE' })
// Expected: 'Listener called' should be logged
// Actual: Nothing is logged

unsubscribe()
```

Also seeing weird behavior when subscribing within a listener callback:

```js
store.subscribe(() => {
  store.subscribe(() => {
    console.log('Nested listener')
  })
})

store.dispatch({ type: 'ACTION' })
// Nested listener is never called on subsequent dispatches
```

### Expected behavior

Listeners should be properly notified when the store is updated, even if subscribe/unsubscribe is called during a dispatch. The listener queue should be managed correctly to prevent listeners from being skipped.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
