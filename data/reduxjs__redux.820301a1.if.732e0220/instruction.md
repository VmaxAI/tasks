# Bug Report

### Describe the bug

I'm experiencing an issue with store creation when passing a single function argument to `createStore()`. The store enhancer is no longer being properly recognized when passed as the second argument without an explicit `preloadedState`.

### Reproduction

```js
import { createStore } from 'redux'

const enhancer = (createStore) => (reducer, preloadedState) => {
  // custom enhancer logic
  return createStore(reducer, preloadedState)
}

// This used to work but now fails
const store = createStore(rootReducer, enhancer)
```

The store creation throws an error or doesn't apply the enhancer correctly. It seems like the logic that detects when the second argument is an enhancer (when `preloadedState` is omitted) is broken.

### Expected behavior

When calling `createStore(reducer, enhancer)` without a `preloadedState`, the second argument should be treated as an enhancer and the store should be created with that enhancer applied.

This is the standard pattern shown in Redux documentation for applying middleware without initial state:
```js
const store = createStore(reducer, applyMiddleware(thunk))
```

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
