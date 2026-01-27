# Bug Report

### Describe the bug

When creating a store with only a reducer and an enhancer function (without providing a preloadedState), the enhancer is not being applied. The store gets created but the enhancer logic is completely ignored.

### Reproduction

```js
import { createStore } from 'redux'

const reducer = (state = {}, action) => state
const enhancer = (createStore) => (reducer, preloadedState) => {
  console.log('Enhancer called')
  return createStore(reducer, preloadedState)
}

// This should apply the enhancer, but it doesn't
const store = createStore(reducer, enhancer)

// Expected: "Enhancer called" to be logged
// Actual: Nothing is logged, enhancer is not invoked
```

### Expected behavior

The enhancer should be recognized and applied when passed as the second argument (when preloadedState is omitted). The store should be created with the enhancer's modifications.

### System Info
- Redux version: latest
- Node version: 18.x

This used to work in previous versions where you could pass an enhancer as the second parameter without providing preloadedState.

---
Repository: /testbed
