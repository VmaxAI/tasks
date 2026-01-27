# Bug Report

### Describe the bug

I'm unable to subscribe to store changes using the `subscribe()` method. Every time I try to add a listener function, it throws an error saying the listener is not a function, even though I'm clearly passing a valid function.

### Reproduction

```js
import { createStore } from 'redux'

const store = createStore(reducer)

// This throws an error
store.subscribe(() => {
  console.log('State changed!')
})
```

The error message says:
```
Expected the listener to be a function. Instead, received: 'function'
```

Which is confusing because I AM passing a function. I've tried with both arrow functions and regular functions, and both fail with the same error.

### Expected behavior

The subscribe method should accept the listener function and call it whenever the store state changes. This used to work fine before.

### System Info
- Redux version: latest
- Node: v18.x

---
Repository: /testbed
