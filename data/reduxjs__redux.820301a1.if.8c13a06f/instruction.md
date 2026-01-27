# Bug Report

### Describe the bug

The store creation is completely broken after the latest update. When trying to create a store with an enhancer (like applyMiddleware), the application crashes immediately.

### Reproduction

```js
import { createStore, applyMiddleware } from 'redux'
import thunk from 'redux-thunk'

const reducer = (state = {}, action) => {
  return state
}

// This throws an error now
const store = createStore(
  reducer,
  applyMiddleware(thunk)
)
```

### Expected behavior

The store should be created successfully with the middleware applied. This was working fine in previous versions but now fails completely.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
