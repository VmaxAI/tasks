# Bug Report

### Describe the bug

I'm encountering an issue with `combineReducers` where it's throwing an error during initialization even when my reducer correctly returns an initial state. The error message says the reducer returned undefined during initialization, but my reducer is definitely returning a valid state object.

### Reproduction

```js
import { combineReducers } from 'redux'

const myReducer = (state = { count: 0 }, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 }
    default:
      return state
  }
}

const rootReducer = combineReducers({
  counter: myReducer
})

// This throws an error about undefined state
const store = createStore(rootReducer)
```

### Expected behavior

The store should initialize successfully since the reducer returns a valid initial state (`{ count: 0 }`) when called with undefined state and the INIT action.

### System Info
- Redux version: latest
- Node version: 18.x

This is blocking me from setting up my store. Any help would be appreciated!

---
Repository: /testbed
