# Bug Report

### Describe the bug

I'm getting an unexpected error when trying to create a Redux store with a preloaded state. The error message says I'm passing multiple store enhancers, but I'm only passing the initial state and no enhancers at all.

### Reproduction

```js
import { createStore } from 'redux'

function reducer(state = {}, action) {
  return state
}

const initialState = { count: 0 }

// This throws an error about multiple store enhancers
const store = createStore(reducer, initialState)
```

The error message I get is:
```
Error: It looks like you are passing several store enhancers to createStore(). This is not supported. Instead, compose them together to a single function.
```

### Expected behavior

The store should be created successfully with the preloaded state. This is a standard pattern that should work according to the Redux documentation.

### Additional context

This seems to happen whenever I pass an object as the second parameter to `createStore`. The validation logic appears to be incorrectly detecting my initial state object as a store enhancer.

---
Repository: /testbed
