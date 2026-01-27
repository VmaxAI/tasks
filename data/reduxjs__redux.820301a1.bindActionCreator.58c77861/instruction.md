# Bug Report

### Describe the bug
When using `bindActionCreators()`, bound action creators are not receiving all their arguments correctly. It seems like the first argument is being dropped when the bound function is called.

### Reproduction
```js
const actionCreator = (id, name, data) => ({
  type: 'UPDATE_USER',
  payload: { id, name, data }
})

const boundAction = bindActionCreators({ updateUser: actionCreator }, dispatch)

// Calling with multiple arguments
boundAction.updateUser(123, 'John', { active: true })

// Expected payload: { id: 123, name: 'John', data: { active: true } }
// Actual payload: { id: 'John', name: { active: true }, data: undefined }
```

The bound action creator seems to skip the first argument and shift all subsequent arguments to the left. This breaks any action creators that rely on multiple parameters.

### Expected behavior
All arguments passed to a bound action creator should be forwarded to the original action creator function without any being dropped or reordered.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
