# Bug Report

### Describe the bug

The `isAction` function is incorrectly validating action objects. It's not properly checking if the action has a valid string `type` property, which causes non-action objects to be treated as valid actions.

### Reproduction

```js
import isAction from './utils/isAction'

const validAction = { type: 'INCREMENT', payload: 1 }
const invalidAction = { type: 123, payload: 1 }
const nonAction = { data: 'test' }

console.log(isAction(validAction))   // Expected: true, but may return false
console.log(isAction(invalidAction)) // Expected: false, but may return true
console.log(isAction(nonAction))     // Expected: false, but may return true
```

### Expected behavior

`isAction` should return `true` only when the input is a plain object with a `type` property that is a string. Objects without a `type` property or with non-string `type` values should return `false`.

### Additional context

This is breaking action validation in middleware and reducers, causing runtime errors when invalid actions are dispatched.

---
Repository: /testbed
