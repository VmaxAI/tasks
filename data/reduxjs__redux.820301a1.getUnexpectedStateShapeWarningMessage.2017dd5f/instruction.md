# Bug Report

### Describe the bug

When using `combineReducers()`, I'm getting warnings about unexpected keys even when the keys are actually valid reducer keys. The warning message is appearing for keys that ARE present in my reducers object, not for keys that are missing.

### Reproduction

```js
import { combineReducers, createStore } from 'redux'

const userReducer = (state = {}, action) => state
const postsReducer = (state = [], action) => state

const rootReducer = combineReducers({
  user: userReducer,
  posts: postsReducer
})

const store = createStore(rootReducer, {
  user: { name: 'test' },
  posts: []
})
```

### Expected behavior

No warnings should be shown since `user` and `posts` are both valid reducer keys. The warning should only appear for keys in the initial state that DON'T match any reducer keys.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
