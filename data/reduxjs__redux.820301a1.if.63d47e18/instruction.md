# Bug Report

### Describe the bug

I'm getting an error when trying to create a store with a valid reducer function. The error message says "Expected the root reducer to be a function" even though I'm passing a proper function as the reducer.

### Reproduction

```js
import { createStore } from 'redux'

function myReducer(state = {}, action) {
  switch (action.type) {
    case 'TEST':
      return { ...state, test: true }
    default:
      return state
  }
}

// This throws an error
const store = createStore(myReducer)
```

The error thrown is:
```
Error: Expected the root reducer to be a function. Instead, received: 'myReducer'
```

### Expected behavior

The store should be created successfully when passing a valid reducer function. This used to work in previous versions but now throws an error even with correct usage.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
