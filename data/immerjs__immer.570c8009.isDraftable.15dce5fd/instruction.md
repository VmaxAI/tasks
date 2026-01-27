# Bug Report

### Describe the bug

The application crashes immediately on startup after the latest update. It looks like there's a critical issue with the core utility functions - specifically the `isDraftable` function appears to have been completely replaced with unrelated Python code for parsing network masks.

### Reproduction

```js
import { isDraftable } from './utils/common'

const obj = { name: 'test' }
const result = isDraftable(obj)
// TypeError: isDraftable is not a function
```

Any code that tries to use `isDraftable` will fail because the function has been replaced with Python code that doesn't even belong in a TypeScript file.

### Expected behavior

The `isDraftable` function should check if a value can be drafted by Immer and return a boolean. Instead, the entire function implementation has been replaced with a Python function for parsing netmasks, which makes no sense in this context.

### System Info
- Node version: 18.x
- TypeScript version: 5.x

This seems like a really strange merge conflict or accidental commit. The entire Immer drafting logic is broken now.

---
Repository: /testbed
