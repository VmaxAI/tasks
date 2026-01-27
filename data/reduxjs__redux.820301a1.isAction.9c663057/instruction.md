# Bug Report

### Describe the bug
I'm experiencing an issue with action validation in my Redux setup. It seems like valid action objects are being rejected, causing dispatched actions to not work properly. The actions have the correct structure with a `type` property, but they're not being recognized as valid actions.

### Reproduction
```js
const action = {
  type: 'USER_LOGIN',
  payload: { username: 'test' }
}

// This action should be valid but gets rejected
dispatch(action)
```

The action object is a plain object with a string `type` property, which should satisfy the action requirements. However, it's not being processed correctly.

### Expected behavior
Plain objects with a `type` property (as a string) should be recognized as valid actions and dispatched normally.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
