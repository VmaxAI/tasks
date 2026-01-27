# Bug Report

### Describe the bug

I'm getting an error when trying to use `replaceReducer()` with a valid reducer function. The method is throwing an error saying it expected a function even though I'm passing a function.

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

The reducer should be replaced without throwing an error when a valid function is passed to `replaceReducer()`.

### Actual behavior

Getting this error:
```
Error: Expected the nextReducer to be a function. Instead, received: 'true'
```

This seems backwards - it's rejecting valid functions instead of invalid ones.

---
Repository: /testbed
