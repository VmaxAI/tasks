# Bug Report

### Describe the bug

I'm experiencing an issue with `createStore` when passing a store enhancer as the second argument without providing an initial state. The store creation seems to be handling the arguments incorrectly, and I'm getting unexpected behavior.

### Reproduction

```js
import { createStore } from 'redux'

const reducer = (state = {}, action) => {
  return state
}

const enhancer = (createStore) => (reducer, preloadedState) => {
  // custom enhancer logic
  return createStore(reducer, preloadedState)
}

// This doesn't work as expected
const store = createStore(reducer, enhancer)
```

When I call `createStore` with just a reducer and an enhancer (no initial state), the enhancer doesn't seem to be applied correctly. Previously, this pattern worked fine where you could omit the `preloadedState` and just pass the enhancer as the second argument.

### Expected behavior

The store should be created with the enhancer applied, even when no initial state is provided. The function should recognize that the second argument is an enhancer and handle it appropriately.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
