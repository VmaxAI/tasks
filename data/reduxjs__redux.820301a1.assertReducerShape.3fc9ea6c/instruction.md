# Bug Report

### Describe the bug

I'm experiencing an issue with `combineReducers` where it's not properly validating reducer behavior during initialization. The validation logic seems to be inverted or incorrect, causing reducers that should pass validation to throw errors, and reducers that should fail validation to be accepted.

### Reproduction

```js
import { combineReducers } from 'redux'

// This reducer correctly returns undefined for unknown actions
const myReducer = (state = { count: 0 }, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 }
    default:
      return state
  }
}

// Trying to combine reducers throws an unexpected error
const rootReducer = combineReducers({
  mySlice: myReducer
})
```

### Expected behavior

Reducers that properly handle the initial state and return a valid state for unknown actions should pass validation without errors. The validation should catch reducers that actually return `undefined` when they shouldn't, not the other way around.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
