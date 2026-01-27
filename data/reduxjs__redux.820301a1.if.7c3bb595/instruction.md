# Bug Report

### Describe the bug

The `subscribe()` method is throwing an error when I pass a valid function as a listener. It seems like the validation logic is backwards - it's rejecting functions when it should be accepting them.

### Reproduction

```js
const store = createStore(reducer, initialState)

// This throws an error but shouldn't
const unsubscribe = store.subscribe(() => {
  console.log('State changed!')
})
```

The error message says:
```
Expected the listener to be a function. Instead, received: 'function'
```

Which is confusing because I *am* passing a function.

### Expected behavior

The subscribe method should accept a function as a listener without throwing an error. The listener should be called whenever the store state changes.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
