# Bug Report

### Describe the bug

I'm encountering an issue with `replaceReducer()` where passing a valid reducer function throws an error instead of accepting it. The error message says it expected a function, but I'm passing a function.

### Reproduction

```js
import { createStore } from 'redux'

const initialReducer = (state = {}, action) => state
const store = createStore(initialReducer)

const newReducer = (state = { count: 0 }, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 }
    default:
      return state
  }
}

// This throws an error even though newReducer is a function
store.replaceReducer(newReducer)
```

### Expected behavior

`replaceReducer()` should accept the new reducer function without throwing an error. The store should use the new reducer for subsequent dispatches.

### Actual behavior

An error is thrown: `Expected the nextReducer to be a function. Instead, received: 'function'`

This makes it impossible to replace reducers dynamically, which is needed for code splitting and hot module replacement scenarios.

---
Repository: /testbed
