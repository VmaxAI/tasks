# Bug Report

### Describe the bug

I'm experiencing an issue with middleware dispatch functionality. When middleware tries to dispatch actions with additional arguments, the arguments are not being passed through correctly. The dispatched action receives an array instead of the individual arguments.

### Reproduction

```js
const middleware = store => next => action => {
  // Try to dispatch with extra arguments
  store.dispatch({ type: 'TEST' }, 'arg1', 'arg2')
  return next(action)
}

const store = createStore(
  reducer,
  applyMiddleware(middleware)
)

// Expected: action handler receives 'arg1', 'arg2' as separate arguments
// Actual: receives an array ['arg1', 'arg2']
```

### Expected behavior

When calling `dispatch(action, ...args)` from within middleware, the additional arguments should be spread and passed through as individual parameters, not wrapped in an array.

### Additional context

This seems to affect any middleware that needs to pass extra parameters along with actions. The dispatch function should preserve the argument spreading behavior.

---
Repository: /testbed
