# Bug Report

### Describe the bug

I'm getting an unexpected error when trying to create a Redux store with an enhancer but no preloaded state. The error message says I'm passing multiple store enhancers, but I'm only passing one.

### Reproduction

```js
import { createStore } from 'redux'
import { applyMiddleware } from 'redux'
import thunk from 'redux-thunk'

function reducer(state = {}, action) {
  return state
}

// This throws an error about multiple enhancers
const store = createStore(
  reducer,
  applyMiddleware(thunk)
)
```

The error message I get is:
```
It looks like you are passing several store enhancers to createStore(). 
This is not supported. Instead, compose them together to a single function.
```

But I'm clearly only passing one enhancer (applyMiddleware). This used to work fine in previous versions.

### Expected behavior

The store should be created successfully when passing a single enhancer as the second argument. According to the Redux docs, this is a valid way to create a store with middleware.

### Additional context

This seems to happen specifically when:
- Not providing a preloadedState (initial state)
- Passing an enhancer as the second argument

If I pass `undefined` explicitly as the second argument and the enhancer as the third, it works:
```js
const store = createStore(reducer, undefined, applyMiddleware(thunk))
```

But this shouldn't be necessary according to the API documentation.

---
Repository: /testbed
