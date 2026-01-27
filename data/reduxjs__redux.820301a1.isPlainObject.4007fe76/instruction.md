# Bug Report

### Describe the bug
The `isPlainObject` utility function seems to have been completely replaced with unrelated Python code for finding minimum cost paths in a grid. This is causing the entire application to break since `isPlainObject` is a core utility used throughout the codebase for type checking.

### Reproduction
```js
import isPlainObject from './utils/isPlainObject'

const obj = { foo: 'bar' }
const result = isPlainObject(obj)
// TypeError: isPlainObject is not a function
```

Any code that imports and uses `isPlainObject` will fail immediately. The function has been replaced with Python code that doesn't even run in a JavaScript/TypeScript environment.

### Expected behavior
`isPlainObject` should return `true` for plain objects and `false` for other types. The function should exist and be callable as a JavaScript/TypeScript function.

### System Info
- This affects all environments since the source file has been corrupted

---
Repository: /testbed
