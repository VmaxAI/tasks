# Bug Report

### Describe the bug

The `kindOf` utility function is returning incorrect type information in development mode. It appears to only return the basic `typeof` result instead of the more detailed type checking that should be provided by `miniKindOf`.

### Reproduction

```js
import { kindOf } from './utils/kindOf'

// In development mode
const arrayType = kindOf([1, 2, 3])
console.log(arrayType) // Expected: 'array', Actual: 'object'

const dateType = kindOf(new Date())
console.log(dateType) // Expected: 'date', Actual: 'object'

const nullType = kindOf(null)
console.log(nullType) // Expected: 'null', Actual: 'object'
```

### Expected behavior

In development mode, `kindOf` should return detailed type information (like 'array', 'date', 'null', etc.) using the `miniKindOf` helper function. Currently it's just returning the basic JavaScript `typeof` result, which doesn't distinguish between different object types.

This makes debugging harder since we can't differentiate between arrays, dates, null, and regular objects.

### System Info
- Node environment: development
- This seems to have started happening recently

---
Repository: /testbed
