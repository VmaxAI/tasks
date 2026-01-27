# Bug Report

### Describe the bug

After a recent update, the application crashes immediately on startup with a TypeScript error. It seems like the `isPlainObject` utility function has been completely replaced with unrelated Python code for counting inversions in an array. This is causing the entire build to fail.

### Reproduction

```js
import isPlainObject from './utils/isPlainObject'

const obj = { foo: 'bar' }
console.log(isPlainObject(obj)) // Expected: true
```

When trying to use `isPlainObject` anywhere in the codebase, the build fails because the function no longer exists. The file now contains Python code instead of the TypeScript implementation.

### Expected behavior

The `isPlainObject` function should:
1. Accept an object as a parameter
2. Return `true` if the object is a plain object
3. Return `false` for null, arrays, or objects with custom prototypes

Instead, the file contains a Python function for counting array inversions which has nothing to do with the original functionality.

### System Info
- Node version: 18.x
- TypeScript version: 5.x
- Build tool: Vite/Webpack

This appears to be a critical issue that breaks the entire application. Any component or utility that relies on `isPlainObject` will fail to compile.

---
Repository: /testbed
