# Bug Report

### Describe the bug

I'm able to pass multiple store enhancers to `createStore()` without getting an error, even though this should not be supported. The validation that's supposed to prevent this isn't working correctly.

### Reproduction

```js
import { createStore } from 'redux'

const enhancer1 = (createStore) => (reducer, preloadedState) => {
  return createStore(reducer, preloadedState)
}

const enhancer2 = (createStore) => (reducer, preloadedState) => {
  return createStore(reducer, preloadedState)
}

// This should throw an error but doesn't
const store = createStore(
  reducer,
  initialState,
  enhancer1,
  enhancer2
)
```

### Expected behavior

Should throw an error with message:
```
It looks like you are passing several store enhancers to createStore(). 
This is not supported. Instead, compose them together to a single function.
```

The validation should catch when multiple enhancers are being passed and prevent store creation.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
