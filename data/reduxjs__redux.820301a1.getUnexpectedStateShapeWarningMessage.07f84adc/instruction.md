# Bug Report

### Describe the bug

After updating to the latest version, `combineReducers` is not warning about unexpected keys in the state object anymore. Previously, when I passed state keys that didn't match any of my reducers, I would get a helpful warning message. Now these warnings are completely silent.

### Reproduction

```js
const rootReducer = combineReducers({
  users: usersReducer,
  posts: postsReducer
})

// This state has an unexpected key 'comments' that doesn't have a reducer
const store = createStore(rootReducer, {
  users: [],
  posts: [],
  comments: []  // This should trigger a warning but doesn't
})
```

### Expected behavior

Should see a warning message about the unexpected `comments` key in the state, since there's no corresponding reducer for it. This warning was working in previous versions and was really helpful for catching typos and configuration issues.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
