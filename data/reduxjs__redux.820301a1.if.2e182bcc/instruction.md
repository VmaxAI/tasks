# Bug Report

### Describe the bug

I'm encountering an issue where `replaceReducer()` is accepting invalid input without throwing an error. Previously, passing a non-function value to `replaceReducer()` would throw a helpful error message, but now it silently accepts any value and causes the store to break in unexpected ways.

### Reproduction

```js
const store = createStore(rootReducer)

// This should throw an error but doesn't
store.replaceReducer(null)

// Or with other non-function values
store.replaceReducer("not a function")
store.replaceReducer({ type: 'object' })
store.replaceReducer(123)
```

After calling `replaceReducer()` with an invalid value, subsequent dispatches fail with cryptic errors instead of getting a clear validation error upfront.

### Expected behavior

`replaceReducer()` should validate that the argument is a function and throw a descriptive error if it's not, similar to how it worked before. This helps catch bugs early rather than having the store fail later with confusing error messages.

### System Info
- Redux version: latest
- Environment: Node.js 18.x

---
Repository: /testbed
