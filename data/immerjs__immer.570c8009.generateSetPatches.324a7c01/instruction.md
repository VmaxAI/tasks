# Bug Report

### Describe the bug

I'm experiencing an issue with Set operations when using Immer's patch generation. After a recent update, any modifications to Set objects (adding or removing elements) are no longer being tracked properly and patches are not generated for these changes.

### Reproduction

```js
import { enablePatches, produceWithPatches } from 'immer'

enablePatches()

const baseState = {
  tags: new Set(['javascript', 'react'])
}

const [nextState, patches, inversePatches] = produceWithPatches(
  baseState,
  draft => {
    draft.tags.delete('react')
    draft.tags.add('typescript')
  }
)

console.log(patches) // Expected patches for Set changes, but getting empty or incorrect output
```

### Expected behavior

The patches array should contain operations reflecting the removal of 'react' and addition of 'typescript' to the Set. The inversePatches should contain the reverse operations to undo these changes.

### Additional context

This was working fine in previous versions. The Set modifications are applied correctly to the state itself, but the patch generation seems broken. Regular object and array patches still work as expected, only Set patches are affected.

---
Repository: /testbed
