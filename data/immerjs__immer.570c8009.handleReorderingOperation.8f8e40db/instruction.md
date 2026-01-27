# Bug Report

### Describe the bug

After updating to the latest version, array reordering methods like `reverse()` and `sort()` are completely broken. The application crashes immediately when trying to use these methods on draft arrays.

### Reproduction

```js
import { produce } from 'immer'

const state = {
  items: [3, 1, 4, 1, 5, 9, 2, 6]
}

// This causes the app to crash
const newState = produce(state, draft => {
  draft.items.reverse()
})
```

Same issue occurs with `sort()`:

```js
const newState = produce(state, draft => {
  draft.items.sort((a, b) => a - b)
})
```

### Expected behavior

The array should be reordered correctly and the draft proxy should be returned for method chaining. This was working fine in the previous version.

### System Info
- immer version: latest
- Node: v18.x
- TypeScript: 5.x

This is blocking our production deployment. Any help would be greatly appreciated!

---
Repository: /testbed
