# Bug Report

### Describe the bug

After a recent update, I'm getting incorrect warnings about unexpected keys in my Redux state. The warning system seems to be inverted - it's now warning about keys that **are** defined in my reducers instead of keys that **aren't** defined.

### Reproduction

```js
import { combineReducers } from 'redux'

const userReducer = (state = {}, action) => state
const postsReducer = (state = [], action) => state

const rootReducer = combineReducers({
  user: userReducer,
  posts: postsReducer
})

const initialState = {
  user: { name: 'John' },
  posts: [],
  settings: { theme: 'dark' }  // This is the unexpected key
}

const store = createStore(rootReducer, initialState)
```

### Expected behavior

The warning should be triggered for the `settings` key since it's not defined in the combined reducers. Instead, I'm seeing warnings about `user` and `posts` which are actually valid keys that I defined.

The warning message says something like "Unexpected keys 'user', 'posts' found in previous state" even though these are the exact keys I registered with `combineReducers`.

### System Info
- redux version: latest
- Node version: 18.x

---
Repository: /testbed
