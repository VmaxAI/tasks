# Bug Report

### Describe the bug
When using `bindActionCreators` with an object containing multiple action creators, the bound actions don't work correctly. The bound action creators seem to be getting mixed up or returning undefined when invoked.

### Reproduction
```js
import { bindActionCreators } from 'redux'

const actionCreators = {
  increment: () => ({ type: 'INCREMENT' }),
  decrement: () => ({ type: 'DECREMENT' }),
  reset: () => ({ type: 'RESET' })
}

const boundActions = bindActionCreators(actionCreators, dispatch)

// Calling these doesn't dispatch the expected actions
boundActions.increment()  // doesn't work as expected
boundActions.decrement()  // doesn't work as expected
boundActions.reset()      // doesn't work as expected
```

### Expected behavior
Each bound action creator should dispatch its corresponding action when called. The bound actions object should have the same keys as the original action creators object, and calling each bound action should properly dispatch the action.

### System Info
- Redux version: latest
- Node version: 18.x

This seems to have started happening recently. The actions used to bind correctly before.

---
Repository: /testbed
