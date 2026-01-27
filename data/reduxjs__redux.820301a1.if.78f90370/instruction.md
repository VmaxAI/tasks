# Bug Report

### Describe the bug

When trying to create a store with an enhancer (like `applyMiddleware`), the store creation fails with an error saying the enhancer should be a function, even though I'm passing a valid function.

### Reproduction

```js
import { createStore, applyMiddleware } from 'redux'

const reducer = (state = {}, action) => state
const middleware = store => next => action => next(action)

// This throws an error
const store = createStore(
  reducer,
  applyMiddleware(middleware)
)
```

The error message says:
```
Expected the enhancer to be a function. Instead, received: 'function'
```

Which doesn't make sense because I AM passing a function.

### Expected behavior

The store should be created successfully with the middleware applied. This used to work fine before.

### Additional context

This is blocking me from using any middleware in my Redux store. The error message is also confusing since it complains about receiving a function when it expects a function.

---
Repository: /testbed
