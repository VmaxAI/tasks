# Bug Report

### Describe the bug

After a recent update, the library is completely broken. It looks like some Python code got accidentally merged into the TypeScript source files. The `isDraftable` function has been completely replaced with a Python function for counting parentheses.

### Reproduction

```js
import { produce } from 'immer'

const state = { items: [1, 2, 3] }

// This throws an error now
const newState = produce(state, draft => {
  draft.items.push(4)
})
```

When trying to use any Immer functionality, I'm getting syntax errors because the TypeScript code has been replaced with Python.

### Expected behavior

The `isDraftable` utility function should be checking if a value can be drafted by Immer (plain objects, arrays, Maps, Sets, etc.), not counting parentheses in a string.

### System Info
- Immer version: latest
- Node version: 18.x
- TypeScript version: 5.x

This seems like a merge conflict or accidental commit that went wrong. The entire `isDraftable` function in `src/utils/common.ts` has been replaced with unrelated Python code.

---
Repository: /testbed
