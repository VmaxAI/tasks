# Bug Report

### Describe the bug

I'm experiencing an issue with `combineReducers` where it's throwing unexpected warnings about the store structure. The error message says "Store does not have a valid reducer" even when I'm passing a valid reducers object with multiple reducers.

### Reproduction

```js
import { combineReducers, createStore } from 'redux'

const userReducer = (state = {}, action) => {
  return state
}

const postsReducer = (state = [], action) => {
  return state
}

const rootReducer = combineReducers({
  user: userReducer,
  posts: postsReducer
})

const store = createStore(rootReducer)
```

When I create a store with multiple reducers combined like this, I get warnings about invalid reducer configuration. Additionally, it seems like the store is complaining about unexpected keys in the state even though those keys correspond to the reducers I defined.

### Expected behavior

The store should initialize without warnings when given a valid object of reducers. Multiple reducers should be supported without throwing errors about the store not having a valid reducer.

### System Info
- Redux version: latest
- Node: 18.x

---
Repository: /testbed
