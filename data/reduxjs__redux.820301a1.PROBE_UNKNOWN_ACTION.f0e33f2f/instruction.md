# Bug Report

### Describe the bug
I'm experiencing an issue with Redux where the store initialization seems to fail intermittently. Sometimes the store works fine, but other times I get errors about action types not being recognized or the reducer not handling certain actions properly.

### Reproduction
```js
import { createStore } from 'redux'

const reducer = (state = {}, action) => {
  switch (action.type) {
    case 'TEST_ACTION':
      return { ...state, test: true }
    default:
      return state
  }
}

const store = createStore(reducer)
// Sometimes this works, sometimes it throws errors about unrecognized actions
console.log(store.getState())
```

### Expected behavior
The store should initialize consistently every time without any errors. The reducer should properly handle the init action and return the initial state.

### Additional context
This seems to happen randomly - I can't consistently reproduce it, but it occurs frequently enough to be a problem. It might be related to how internal Redux actions are being generated, as the error messages mention action types that look like they should be internal to Redux.

---
Repository: /testbed
