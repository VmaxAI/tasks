# Bug Report

### Describe the bug

I'm experiencing an issue with `bindActionCreators` where action creators that accept arguments are not working properly. The bound action creator seems to ignore any arguments passed to it.

### Reproduction

```js
const actionCreator = (id, name) => ({
  type: 'UPDATE_USER',
  payload: { id, name }
})

const boundAction = bindActionCreators({ updateUser: actionCreator }, dispatch)

// Arguments are not being passed through correctly
boundAction.updateUser(123, 'John')
// Expected: dispatch({ type: 'UPDATE_USER', payload: { id: 123, name: 'John' } })
// Actual: Arguments seem to be lost/ignored
```

### Expected behavior

When calling a bound action creator with arguments, those arguments should be passed to the original action creator function before dispatching the result.

### System Info
- Redux version: latest
- Environment: Node.js

---
Repository: /testbed
