# Bug Report

### Describe the bug

After updating to the latest version, `createStore()` is throwing unexpected errors or behaving strangely when trying to create a Redux store. It seems like some validation logic for store enhancers has been removed or corrupted.

### Reproduction

```js
import { createStore } from 'redux'

const reducer = (state = {}, action) => state
const enhancer1 = (createStore) => (reducer, preloadedState) => {
  return createStore(reducer, preloadedState)
}
const enhancer2 = (createStore) => (reducer, preloadedState) => {
  return createStore(reducer, preloadedState)
}

// This should throw an error about passing multiple enhancers
// but the validation seems to be missing now
const store = createStore(reducer, {}, enhancer1, enhancer2)
```

### Expected behavior

When passing multiple store enhancers directly to `createStore()`, it should throw a clear error message telling users to compose them together instead. The error message should reference the documentation about using `compose()` for multiple enhancers.

The store creation process should validate the arguments properly and provide helpful error messages when used incorrectly.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
