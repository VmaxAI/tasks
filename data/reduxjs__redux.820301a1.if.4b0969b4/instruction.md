# Bug Report

### Describe the bug

I'm getting an unexpected error when trying to create a Redux store with multiple enhancers. The error message says "It looks like you are passing several store enhancers to createStore()" but I'm only passing a single composed enhancer function.

### Reproduction

```js
import { createStore, applyMiddleware, compose } from 'redux'
import thunk from 'redux-thunk'

const rootReducer = (state = {}, action) => state

// Compose multiple enhancers into one
const composedEnhancer = compose(
  applyMiddleware(thunk),
  // some other enhancer
)

// This throws an error about passing several store enhancers
const store = createStore(
  rootReducer,
  composedEnhancer
)
```

### Expected behavior

The store should be created successfully when passing a single composed enhancer. The error about multiple enhancers should only appear when actually passing multiple separate enhancer arguments, not when passing one composed enhancer.

### Additional context

This seems to have started happening recently. The compose pattern is documented in the Redux tutorials, so this should be a supported use case.

---
Repository: /testbed
