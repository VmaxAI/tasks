# Bug Report

### Describe the bug

I think there's a problem with the middleware initialization in `applyMiddleware`. When I try to use middleware that dispatches actions during setup, the store seems to behave unexpectedly. 

### Reproduction

```js
import { createStore, applyMiddleware } from 'redux'

const myMiddleware = store => next => action => {
  // Middleware logic here
  return next(action)
}

const store = createStore(
  reducer,
  applyMiddleware(myMiddleware)
)

// Store doesn't work as expected
store.dispatch({ type: 'TEST_ACTION' })
```

### Expected behavior

The middleware should be properly initialized and actions should be dispatched correctly through the middleware chain. The store should function normally after being created with `applyMiddleware`.

### System Info
- Redux version: latest
- Node version: 18.x

Not sure what's causing this but it seems like something changed in how middleware gets set up. Any help would be appreciated!

---
Repository: /testbed
