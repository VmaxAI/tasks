# Bug Report

### Describe the bug

I'm experiencing an issue where dispatching actions during middleware construction doesn't throw an error as expected. The middleware setup completes without any warning or error being raised, but this should be prevented according to the Redux middleware guidelines.

### Reproduction

```js
const problematicMiddleware = ({ dispatch }) => {
  // This should throw an error but doesn't
  dispatch({ type: 'INIT_ACTION' })
  
  return next => action => {
    return next(action)
  }
}

const store = createStore(
  reducer,
  applyMiddleware(problematicMiddleware)
)
```

### Expected behavior

An error should be thrown with the message: "Dispatching while constructing your middleware is not allowed. Other middleware would not be applied to this dispatch."

Currently, the dispatch call during middleware construction silently fails without throwing an error, which makes it difficult to catch this mistake during development.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
