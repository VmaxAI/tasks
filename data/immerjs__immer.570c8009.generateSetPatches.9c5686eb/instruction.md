# Bug Report

### Describe the bug

After a recent update, Set operations are no longer generating patches correctly. When adding or removing items from a Set inside an Immer draft, the patches array remains empty and no changes are tracked.

### Reproduction

```js
import {produce, enablePatches} from 'immer'

enablePatches()

const baseState = {
  tags: new Set(['javascript', 'react'])
}

const [nextState, patches, inversePatches] = produce(
  baseState,
  draft => {
    draft.tags.delete('react')
    draft.tags.add('typescript')
  },
  (patches, inversePatches) => {
    console.log('Patches:', patches)
    console.log('Inverse patches:', inversePatches)
  }
)

// Expected: patches should contain operations for the Set changes
// Actual: patches array is empty
```

### Expected behavior

The patches should include:
- A REMOVE operation for deleting 'react' from the Set
- An ADD operation for adding 'typescript' to the Set

The inverse patches should contain the reverse operations to undo these changes.

### System Info
- Immer version: latest
- Node version: 18.x

This is blocking our undo/redo functionality which relies on patches for Set operations. Any help would be appreciated!

---
Repository: /testbed
