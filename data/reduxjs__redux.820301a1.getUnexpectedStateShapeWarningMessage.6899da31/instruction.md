# Bug Report

### Describe the bug

After a recent update, the store is throwing errors about unexpected state shape warnings. It seems like the validation logic for checking state shape against reducers has been completely removed or replaced with something unrelated.

### Reproduction

```js
import { combineReducers, createStore } from 'redux'

const userReducer = (state = {}, action) => {
  return state
}

const rootReducer = combineReducers({
  user: userReducer
})

// This should warn about unexpected keys but doesn't anymore
const store = createStore(rootReducer, {
  user: {},
  extraKey: 'this should trigger a warning'
})
```

### Expected behavior

The store should validate the state shape and warn when there are unexpected keys in the state that don't match the combined reducers. Previously, this would log a helpful warning message about unexpected keys found in the state.

Now it seems like this validation is completely gone and the store accepts any state shape without warnings.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
