# Bug Report

### Describe the bug

When trying to create a store with an enhancer (like middleware or devtools), the store creation fails with an error saying the enhancer is not a function, even though a valid function is being passed.

### Reproduction

```js
import { createStore, applyMiddleware } from 'redux'

const reducer = (state = {}, action) => state

// This throws an error even though applyMiddleware returns a valid enhancer function
const store = createStore(
  reducer,
  applyMiddleware(someMiddleware)
)
```

The error message says:
```
Expected the enhancer to be a function. Instead, received: 'function'
```

### Expected behavior

The store should be created successfully when a valid enhancer function is provided. The enhancer should wrap the store creation process and return an enhanced store.

### Additional context

This seems to affect any use case where enhancers are used, including:
- Using `applyMiddleware()`
- Integrating Redux DevTools
- Any custom store enhancers

The store creation works fine when no enhancer is provided, but fails immediately when trying to use any enhancer.

---
Repository: /testbed
