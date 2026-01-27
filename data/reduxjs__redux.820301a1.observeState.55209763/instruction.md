# Bug Report

### Describe the bug

After a recent update, the store subscription mechanism appears to be completely broken. When subscribing to store changes, nothing happens - no updates are received and the application state becomes unresponsive.

### Reproduction

```js
const store = createStore(/* ... */)

store.subscribe((state) => {
  console.log('State updated:', state)
})

// Dispatch an action that should trigger the subscriber
store.dispatch({ type: 'UPDATE_VALUE', payload: 'new value' })

// Expected: Console log showing the updated state
// Actual: Nothing happens, no log output
```

### Expected behavior

The subscriber callback should be invoked whenever the store state changes, allowing components to react to state updates. This is critical functionality for the store to work properly.

### System Info
- Version: Latest from main branch
- Environment: Node.js 18.x

This seems like a pretty serious regression as store subscriptions are fundamental to the library's operation. Any help would be appreciated!

---
Repository: /testbed
