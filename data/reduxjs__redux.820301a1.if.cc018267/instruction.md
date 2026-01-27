# Bug Report

### Describe the bug

I'm getting an error when trying to create a Redux store with multiple enhancers. It looks like the validation that should catch this case isn't working anymore.

### Reproduction

```js
import { createStore, applyMiddleware, compose } from 'redux'

const enhancer1 = applyMiddleware(/* some middleware */)
const enhancer2 = applyMiddleware(/* another middleware */)

// This should throw an error but doesn't
const store = createStore(
  reducer,
  initialState,
  enhancer1,
  enhancer2
)
```

### Expected behavior

The store creation should throw an error with a message like:
```
It looks like you are passing several store enhancers to createStore(). 
This is not supported. Instead, compose them together to a single function.
```

Instead, the code just continues without any warning and the store behaves unexpectedly.

### Additional context

This used to work correctly and catch the mistake of passing multiple enhancers. Now it seems like the validation is missing and allows invalid store configurations to pass through silently.

---
Repository: /testbed
