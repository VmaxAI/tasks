# Bug Report

### Describe the bug

After updating to the latest version, I'm getting an error when trying to create a store with a valid reducer function. The store creation is failing with an error message saying "Expected the root reducer to be a function" even though I'm passing a function as the reducer.

### Reproduction

```js
import { createStore } from 'redux'

const reducer = (state = {}, action) => {
  switch (action.type) {
    case 'TEST':
      return { ...state, test: true }
    default:
      return state
  }
}

// This throws an error now
const store = createStore(reducer)
```

### Expected behavior

The store should be created successfully when passing a valid reducer function. This was working fine in previous versions.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
