# Bug Report

### Describe the bug

I'm getting an error when trying to create a Redux store with a valid reducer function. The error message says "Expected the root reducer to be a function" even though I'm passing a proper function as the reducer.

### Reproduction

```js
import { createStore } from 'redux'

function counterReducer(state = 0, action) {
  switch (action.type) {
    case 'INCREMENT':
      return state + 1
    case 'DECREMENT':
      return state - 1
    default:
      return state
  }
}

// This throws an error
const store = createStore(counterReducer)
```

The error thrown is:
```
Error: Expected the root reducer to be a function. Instead, received: 'function'
```

### Expected behavior

The store should be created successfully when a valid reducer function is provided. This is basic Redux functionality that should work.

### System Info
- Redux version: latest
- Node version: 18.x

This seems like a regression because this exact code was working fine before. Any help would be appreciated!

---
Repository: /testbed
