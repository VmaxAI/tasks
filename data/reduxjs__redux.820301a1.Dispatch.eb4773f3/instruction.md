# Bug Report

### Describe the bug

I'm experiencing an issue with middleware initialization where dispatching actions during middleware construction doesn't properly throw an error. Instead of preventing the dispatch and alerting the developer to the problem, the dispatch silently returns `undefined` without any error being raised.

### Reproduction

```js
const middleware = store => next => action => {
  // This should throw an error but doesn't
  store.dispatch({ type: 'SOME_ACTION' })
  return next(action)
}

const store = createStore(
  reducer,
  applyMiddleware(middleware)
)
```

### Expected behavior

When attempting to dispatch an action during middleware construction, an error should be thrown with the message:
```
'Dispatching while constructing your middleware is not allowed. Other middleware would not be applied to this dispatch.'
```

This is important for catching bugs early during development. Currently, the dispatch just silently fails and returns `undefined`, making it harder to debug issues with middleware setup.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
