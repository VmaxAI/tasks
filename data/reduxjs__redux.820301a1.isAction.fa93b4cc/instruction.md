# Bug Report

### Describe the bug

The `isAction` utility function is not correctly validating action objects. It's accepting objects that shouldn't be considered valid actions, which is causing issues in my middleware and reducers.

### Reproduction

```js
import { isAction } from 'redux'

// This should return false but returns true
const result1 = isAction({ type: 123 })
console.log(result1) // Expected: false, Actual: true

// This should return false but returns true  
const result2 = isAction({ notType: 'test' })
console.log(result2) // Expected: false, Actual: true

// This should return false but returns true
const result3 = isAction('just a string')
console.log(result3) // Expected: false, Actual: true
```

### Expected behavior

`isAction` should only return `true` for objects that:
1. Are plain objects
2. Have a `type` property
3. The `type` property is a string

Any object missing these requirements should return `false`.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
