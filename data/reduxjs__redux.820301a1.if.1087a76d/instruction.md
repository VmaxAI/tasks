# Bug Report

### Describe the bug

When passing a store enhancer to `createStore()`, I'm getting a runtime error saying it expects a function but received an object, even though I'm passing a valid function. The store doesn't get created and the enhancer is never applied.

### Reproduction

```js
import { createStore, applyMiddleware } from 'redux'
import thunk from 'redux-thunk'

const reducer = (state = {}, action) => state

// This throws an error
const store = createStore(
  reducer,
  applyMiddleware(thunk)
)
```

The error message says:
```
Expected the enhancer to be a function. Instead, received: 'function'
```

This is confusing because I am passing a function (the result of `applyMiddleware()`), but the error claims it's not a function.

### Expected behavior

The store should be created successfully with the enhancer applied. The enhancer validation should correctly identify functions and allow them through.

### System Info
- Redux version: latest
- Node version: 18.x

This was working fine before, not sure what changed. Any help would be appreciated!

---
Repository: /testbed
