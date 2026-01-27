# Bug Report

### Describe the bug

When trying to use a store enhancer (middleware), I'm getting an unexpected error message saying it should be a function, but the error is thrown even when I'm passing a valid function. Additionally, when the enhancer is actually called, the arguments seem to be in the wrong order - the reducer and preloadedState appear to be swapped.

### Reproduction

```js
import { createStore } from 'redux'

const myEnhancer = (createStore) => (reducer, preloadedState) => {
  console.log('Reducer:', reducer)
  console.log('PreloadedState:', preloadedState)
  return createStore(reducer, preloadedState)
}

const reducer = (state = { count: 0 }, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 }
    default:
      return state
  }
}

const initialState = { count: 5 }

// This throws an error about enhancer not being a function
const store = createStore(reducer, initialState, myEnhancer)
```

### Expected behavior

The enhancer should be accepted as a valid function, and when called, it should receive the arguments in the correct order: `(reducer, preloadedState)`.

### Additional context

This seems to have broken recently. The error message says the enhancer should be a function, but I'm definitely passing a function. Also, when I debug the enhancer callback, the arguments are backwards - what should be the reducer is actually the preloadedState and vice versa.

---
Repository: /testbed
