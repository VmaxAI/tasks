# Bug Report

### Describe the bug

After a recent update, the middleware chain is completely broken. When trying to use any middleware with `applyMiddleware()`, I'm getting syntax errors and the store fails to initialize.

### Reproduction

```js
import { createStore, applyMiddleware } from 'redux'
import thunk from 'redux-thunk'

const store = createStore(
  rootReducer,
  applyMiddleware(thunk)
)

// Store creation fails with syntax error
```

### Expected behavior

The middleware should be applied correctly and the store should initialize without errors. The `dispatch` function should be properly wrapped by the middleware chain.

### System Info
- Redux version: latest
- Node version: 18.x

This is blocking our production deployment. Any help would be appreciated!

---
Repository: /testbed
