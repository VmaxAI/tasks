# Bug Report

### Describe the bug

I'm experiencing an issue with `combineReducers` where it's incorrectly flagging reducer keys as unexpected when they exist in the state but have falsy values (like `0`, `false`, empty string, etc.).

### Reproduction

```js
import { combineReducers } from 'redux'

const reducers = {
  counter: (state = 0) => state,
  isEnabled: (state = false) => state,
  message: (state = '') => state
}

const rootReducer = combineReducers(reducers)

// This triggers unexpected key warnings even though the keys are valid
const state = {
  counter: 0,
  isEnabled: false,
  message: ''
}
```

When the state contains keys with falsy values like `0`, `false`, or empty strings, I'm getting warnings about "unexpected keys" even though these are legitimate reducer keys. The warning message appears to be checking the truthiness of the reducer value instead of checking if the key actually exists in the reducers object.

### Expected behavior

`combineReducers` should only warn about truly unexpected keys that don't correspond to any registered reducer, regardless of whether the reducer's current value is falsy or not. Keys that map to valid reducers should never trigger the unexpected key warning.

### Additional context

This seems to affect any scenario where a reducer might return a falsy value, which is pretty common (counters starting at 0, boolean flags, empty strings, etc.).

---
Repository: /testbed
