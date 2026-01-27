# Bug Report

### Describe the bug

I'm experiencing an issue where action validation is accepting objects that shouldn't be valid actions. Specifically, actions created from class instances or other non-plain objects are now passing validation when they shouldn't.

### Reproduction

```js
class CustomAction {
  type = 'CUSTOM_ACTION'
  payload = { data: 'test' }
}

const action = new CustomAction()

// This is incorrectly treated as a valid action
// even though it's not a plain object
dispatch(action)
```

The action validator seems to be accepting any object with a `type` property, regardless of whether it's a plain object or an instance of a class. This could lead to unexpected behavior when using class instances or other object types that weren't intended to be actions.

### Expected behavior

Only plain objects should be accepted as valid actions. Class instances and other non-plain objects should be rejected during validation.

### System Info
- Redux version: latest
- Environment: Node.js 18

---
Repository: /testbed
