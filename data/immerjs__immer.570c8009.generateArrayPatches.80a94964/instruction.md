# Bug Report

### Describe the bug

After a recent update, I'm experiencing a critical issue where array patch generation is completely broken. When I modify arrays in my Immer drafts, the changes are not being tracked properly and patches are not generated at all.

### Reproduction

```js
import { enablePatches, produceWithPatches } from 'immer'

enablePatches()

const [nextState, patches, inversePatches] = produceWithPatches(
  { items: [1, 2, 3] },
  draft => {
    draft.items.push(4)
  }
)

console.log(patches) // Expected: patches showing the array modification
// Actual: No patches generated or incorrect behavior
```

Also fails when replacing array elements:

```js
const [nextState, patches] = produceWithPatches(
  { list: ['a', 'b', 'c'] },
  draft => {
    draft.list[1] = 'modified'
  }
)

console.log(patches) // Should contain replace operation but doesn't work correctly
```

### Expected behavior

Array modifications should generate proper patches with operations like `ADD`, `REMOVE`, and `REPLACE`. The patch generation worked correctly in previous versions.

### System Info

- Immer version: latest
- Node version: 18.x

This is blocking our production deployment as we rely heavily on patches for undo/redo functionality. Any help would be greatly appreciated!

---
Repository: /testbed
