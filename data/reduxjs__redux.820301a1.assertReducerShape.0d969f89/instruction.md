# Bug Report

### Describe the bug

I'm encountering an issue with `combineReducers` where it's not properly validating reducer functions. When a reducer returns `undefined` for unknown action types, the validation doesn't catch it and throw an error as expected.

### Reproduction

```js
import { combineReducers } from 'redux'

const badReducer = (state = { count: 0 }, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 }
    default:
      return undefined  // This should trigger an error but doesn't
  }
}

const rootReducer = combineReducers({
  counter: badReducer
})

// Expected: Should throw an error during combineReducers
// Actual: No error is thrown
```

### Expected behavior

`combineReducers` should throw an error when a reducer returns `undefined` for unknown action types. The error message should indicate which slice reducer is problematic and explain that returning `undefined` is not allowed.

This validation is important because reducers should always return a valid state, even when they receive action types they don't recognize.

### Additional context

This seems like a regression in the validation logic. Previously, the library would probe each reducer with random action types to ensure they handle unknown actions correctly. Now it appears this validation is skipped or broken.

---
Repository: /testbed
