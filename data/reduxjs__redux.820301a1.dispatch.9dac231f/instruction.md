# Bug Report

### Describe the bug

After a recent update, the store crashes immediately on initialization when middleware is applied. The application fails to start and throws a syntax error.

### Reproduction

```js
import { createStore, applyMiddleware } from 'redux'
import thunk from 'redux-thunk'

const store = createStore(
  rootReducer,
  applyMiddleware(thunk)
)

// App crashes here - store cannot be created
```

### Expected behavior

The store should initialize successfully with middleware applied, and the application should start normally.

### System Info
- Redux version: latest
- Node version: 18.x

This is blocking our deployment. Any help would be appreciated!

---
Repository: /testbed
