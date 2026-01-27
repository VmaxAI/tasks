# Bug Report

### Describe the bug

After a recent update, patches are no longer being generated correctly for nested state changes. When modifying deeply nested properties in drafts, the patches either contain incorrect paths or fail to be generated entirely.

### Reproduction

```js
import {produce, enablePatches} from 'immer'

enablePatches()

const baseState = {
  users: {
    123: {
      profile: {
        name: 'John'
      }
    }
  }
}

const [nextState, patches] = produce(
  baseState,
  draft => {
    draft.users[123].profile.name = 'Jane'
  },
  (patches, inversePatches) => {
    console.log('Patches:', patches)
    // Expected: patches with correct path to users.123.profile.name
    // Actual: patches are empty or have wrong paths
  }
)
```

### Expected behavior

Patches should be generated with the correct path for nested property changes. The path should accurately reflect the location of the modified property in the state tree.

### System Info
- immer version: latest
- Node version: 18.x

This is breaking our undo/redo functionality which relies on patches to track state changes. Any nested modifications are not being tracked properly.

---
Repository: /testbed
