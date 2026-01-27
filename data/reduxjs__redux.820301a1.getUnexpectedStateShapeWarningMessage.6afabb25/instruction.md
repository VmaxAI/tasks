# Bug Report

### Describe the bug

I'm getting unexpected warnings about state shape when using `combineReducers()`. The warning appears even when all my reducers are properly defined and the state keys match the reducer keys exactly.

### Reproduction

```js
import { combineReducers, createStore } from 'redux'

const userReducer = (state = {}, action) => state
const postsReducer = (state = [], action) => state

const rootReducer = combineReducers({
  user: userReducer,
  posts: postsReducer
})

const store = createStore(rootReducer)

// This triggers a warning about unexpected keys in state shape
// even though 'user' and 'posts' are both defined reducers
store.dispatch({ type: 'SOME_ACTION' })
```

The warning message claims that keys in my state are unexpected, but they're all valid reducer keys. This seems backwards - it's warning about keys that SHOULD be there instead of keys that shouldn't.

### Expected behavior

No warnings should appear when the state shape matches the combined reducers. Warnings should only appear for keys that exist in the state but don't have a corresponding reducer.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
