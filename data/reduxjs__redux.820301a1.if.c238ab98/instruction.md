# Bug Report

### Describe the bug

The `replaceReducer` method is throwing an error when passed a valid function reducer. It seems like the validation logic is inverted - it's rejecting functions instead of accepting them.

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

// This throws an error even though newReducer is a valid function
store.replaceReducer(newReducer)
```

### Expected behavior

`replaceReducer` should accept a valid reducer function without throwing an error. The new reducer should replace the old one and the store should work normally with the new reducer.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
