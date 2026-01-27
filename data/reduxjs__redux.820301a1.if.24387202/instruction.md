# Bug Report

### Describe the bug

When trying to create a Redux store with multiple enhancers passed as separate arguments, the error validation is not working. The store gets created without throwing the expected error message about passing several store enhancers.

### Reproduction

```js
import { createStore } from 'redux'

const reducer = (state = {}, action) => state
const enhancer1 = next => next
const enhancer2 = next => next
const enhancer3 = next => next

// This should throw an error but doesn't
const store = createStore(
  reducer,
  {},
  enhancer1,
  enhancer2
)
```

### Expected behavior

Should throw an error with message:
```
It looks like you are passing several store enhancers to createStore(). 
This is not supported. Instead, compose them together to a single function.
```

According to the Redux documentation, multiple enhancers should be composed together using `compose()` before being passed to `createStore()`. The validation that catches this mistake seems to be missing.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
