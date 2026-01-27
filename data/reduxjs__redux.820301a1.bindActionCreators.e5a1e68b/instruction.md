# Bug Report

### Describe the bug

When using `bindActionCreators`, the returned object doesn't contain the bound action creators. Instead, it returns the original action creators object, which means dispatching actions through the bound creators doesn't work as expected.

### Reproduction

```js
import { bindActionCreators } from 'redux'

const actionCreators = {
  increment: () => ({ type: 'INCREMENT' }),
  decrement: () => ({ type: 'DECREMENT' })
}

const dispatch = (action) => {
  console.log('Dispatched:', action)
}

const boundActions = bindActionCreators(actionCreators, dispatch)

// This should dispatch the action, but nothing happens
boundActions.increment()
```

### Expected behavior

Calling `boundActions.increment()` should automatically dispatch the action through the provided dispatch function. The bound action creators should wrap the original action creators with dispatch calls.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
