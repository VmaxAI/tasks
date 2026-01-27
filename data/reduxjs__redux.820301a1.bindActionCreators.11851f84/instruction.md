# Bug Report

### Describe the bug

I'm experiencing an issue with `bindActionCreators` where it's not correctly binding action creators. When I pass an object with action creator functions, the binding doesn't work as expected and the returned object seems to be empty or incorrect.

### Reproduction

```js
import { bindActionCreators } from 'redux'

const actionCreators = {
  increment: () => ({ type: 'INCREMENT' }),
  decrement: () => ({ type: 'DECREMENT' })
}

const dispatch = (action) => console.log(action)

const boundActions = bindActionCreators(actionCreators, dispatch)

// boundActions is not what I expected
console.log(boundActions) // Expected both increment and decrement to be bound
boundActions.increment() // This doesn't work properly
```

### Expected behavior

The `bindActionCreators` function should return an object where each action creator is wrapped with `dispatch`, so calling `boundActions.increment()` would automatically dispatch the action.

### Additional context

This seems to have started happening recently. Previously this code was working fine. The bound action creators object either appears empty or the functions aren't being bound correctly.

---
Repository: /testbed
