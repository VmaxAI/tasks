# Bug Report

### Describe the bug

When calling `replaceReducer()` with an invalid argument (not a function), the error message is misleading and doesn't properly validate the input. The store accepts non-function values when it should reject them.

### Reproduction

```js
import { createStore } from 'redux'

const initialReducer = (state = {}, action) => state
const store = createStore(initialReducer)

// This should throw an error but doesn't behave correctly
store.replaceReducer({ type: 'NOT_A_FUNCTION' })
```

### Expected behavior

`replaceReducer()` should only accept a function as an argument. When passed a non-function value (like an object, string, number, etc.), it should throw a clear error message indicating that a function was expected.

Currently the validation seems broken - it either accepts invalid values or shows confusing error messages.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
