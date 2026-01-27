# Bug Report

### Describe the bug
When using middleware with `applyMiddleware()`, dispatching actions from within middleware doesn't work correctly. The middleware receives an action but it seems to be called as a function instead of being dispatched properly.

### Reproduction
```js
const customMiddleware = store => next => action => {
  // Try to dispatch another action from middleware
  store.dispatch({ type: 'SECONDARY_ACTION', payload: 'test' })
  return next(action)
}

const store = createStore(
  reducer,
  applyMiddleware(customMiddleware)
)

// This throws an error - action is not a function
store.dispatch({ type: 'PRIMARY_ACTION' })
```

### Expected behavior
Middleware should be able to dispatch actions using `store.dispatch()` without errors. The dispatched action should go through the middleware chain normally.

### Additional context
This used to work in previous versions. Now when middleware tries to dispatch an action, I'm getting errors about the action not being a function or arguments being passed incorrectly.

---
Repository: /testbed
