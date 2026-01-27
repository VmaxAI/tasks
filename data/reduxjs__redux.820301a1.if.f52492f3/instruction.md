# Bug Report

### Describe the bug

The `subscribe()` method is accepting invalid listener arguments without throwing an error. When I try to pass something that's not a function (like a string or number), it doesn't validate the input and causes unexpected behavior later.

### Reproduction

```js
const store = createStore(reducer, initialState)

// This should throw an error but doesn't
store.subscribe("not a function")
store.subscribe(123)
store.subscribe(null)
```

### Expected behavior

The `subscribe()` method should validate that the listener argument is actually a function and throw a descriptive error message if it's not. Previously this worked correctly and would throw an error like:

```
Expected the listener to be a function. Instead, received: 'string'
```

Now it just silently accepts invalid arguments which leads to runtime errors when trying to notify listeners.

### System Info
- Redux version: latest
- Environment: Node.js

---
Repository: /testbed
