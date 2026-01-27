# Bug Report

### Describe the bug

The `kindOf` utility function is returning incorrect type information in development mode. When I call `kindOf()` on various values, it's just returning the basic JavaScript `typeof` result instead of the more detailed type information that it should provide.

### Reproduction

```js
import { kindOf } from './utils/kindOf'

// These all return basic typeof results instead of detailed types
console.log(kindOf(new Date()))  // Returns "object" instead of "date"
console.log(kindOf([1, 2, 3]))   // Returns "object" instead of "array"
console.log(kindOf(null))        // Returns "object" instead of "null"
```

### Expected behavior

In development mode, `kindOf` should return more specific type information (like "date", "array", "null", etc.) instead of just the basic JavaScript `typeof` results. This is important for debugging and error messages during development.

### System Info
- Node environment: development
- Running in non-production mode

---
Repository: /testbed
