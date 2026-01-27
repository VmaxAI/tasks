# Bug Report

### Describe the bug

When passing multiple store enhancers to `createStore()`, the validation that should throw an error is not working correctly. The store is created without any error even though multiple enhancers are being passed, which is not supported and can lead to unexpected behavior.

### Reproduction

```js
import { createStore } from 'redux'

const enhancer1 = (createStore) => (reducer, preloadedState) => {
  // enhancer logic
  return createStore(reducer, preloadedState)
}

const enhancer2 = (createStore) => (reducer, preloadedState) => {
  // enhancer logic
  return createStore(reducer, preloadedState)
}

const reducer = (state = {}, action) => state

// This should throw an error but doesn't
const store = createStore(reducer, enhancer1, enhancer2)
```

### Expected behavior

An error should be thrown with the message: "It looks like you are passing several store enhancers to createStore(). This is not supported. Instead, compose them together to a single function."

The validation should catch when multiple enhancers are being passed and prevent the store from being created incorrectly.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
