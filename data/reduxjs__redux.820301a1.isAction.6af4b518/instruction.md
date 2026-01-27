# Bug Report

### Describe the bug

Actions created with custom prototypes or class instances are not being recognized as valid actions. The validation logic seems to reject objects that aren't plain objects, even when they have the correct `type` property.

### Reproduction

```js
class CustomAction {
  constructor(type) {
    this.type = type;
  }
}

const action = new CustomAction('UPDATE_USER');

// This action is not recognized as valid
// even though it has a type property with a string value
dispatch(action);
```

Another case:
```js
const actionProto = { type: 'CUSTOM_ACTION' };
const action = Object.create(actionProto);

// This also fails validation
dispatch(action);
```

### Expected behavior

Any object with a `type` property containing a string should be considered a valid action, regardless of whether it's a plain object or has a custom prototype chain.

### System Info
- Version: latest
- Environment: Node.js

---
Repository: /testbed
