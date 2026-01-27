# Bug Report

### Describe the bug

When calling `createStore` with only a reducer and an enhancer function (without explicitly passing `undefined` for the preloadedState), the store creation fails or behaves unexpectedly. It seems like the enhancer parameter isn't being recognized properly when preloadedState is omitted.

### Reproduction

```js
import { createStore } from 'redux'

const reducer = (state = {}, action) => state
const enhancer = (createStore) => (reducer, preloadedState) => {
  const store = createStore(reducer, preloadedState)
  return store
}

// This doesn't work as expected
const store = createStore(reducer, enhancer)
```

The issue occurs when you want to pass an enhancer as the second argument without providing a preloadedState. Previously this worked fine, but now it seems to require explicitly passing `undefined` as the second parameter:

```js
// Workaround - have to explicitly pass undefined
const store = createStore(reducer, undefined, enhancer)
```

### Expected behavior

`createStore(reducer, enhancer)` should work correctly and recognize the second parameter as an enhancer when it's a function and no third parameter is provided. The store should be created with the enhancer applied.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
