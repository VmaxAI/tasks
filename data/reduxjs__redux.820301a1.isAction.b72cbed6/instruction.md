# Bug Report

### Describe the bug

The `isAction` function is now accepting actions with non-string `type` properties. Previously, it would only validate actions that had a string type, but now it's allowing any defined value for the type field.

### Reproduction

```js
import { isAction } from './utils/isAction'

// This should return false but now returns true
const invalidAction = {
  type: 123,
  payload: 'data'
}

console.log(isAction(invalidAction)) // Expected: false, Actual: true

// Another case that shouldn't be valid
const anotherInvalid = {
  type: null,
  data: 'test'
}

console.log(isAction(anotherInvalid)) // Expected: false, Actual: true
```

### Expected behavior

`isAction` should only return `true` for objects where the `type` property is explicitly a string. Actions with numeric types, null types, or other non-string types should be rejected.

### Additional context

This seems to have changed recently. The validation is now too permissive and could lead to runtime errors when code expects action types to always be strings.

---
Repository: /testbed
