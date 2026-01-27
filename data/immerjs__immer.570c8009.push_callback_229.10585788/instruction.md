# Bug Report

### Describe the bug

I'm experiencing a critical issue with cross-reference handling in the latest version. When working with nested draft objects that have cross-references between different scopes, the finalization process seems to be completely broken.

### Reproduction

```js
import { produce } from 'immer'

const baseState = {
  items: [
    { id: 1, name: 'Item 1' },
    { id: 2, name: 'Item 2' }
  ],
  selectedItem: null
}

// Create a cross-reference
const nextState = produce(baseState, draft => {
  draft.selectedItem = draft.items[0]
  draft.items[0].name = 'Updated Item 1'
})

console.log(nextState.selectedItem.name)
// Expected: 'Updated Item 1'
// Actual: Error or unexpected behavior
```

### Expected behavior

When a draft object contains cross-references to other parts of the draft tree, those references should be properly updated with the finalized values after the produce function completes. The cross-reference cleanup callback should update the target location with the finalized value.

### Additional context

This appears to affect any scenario where:
1. You have nested objects in a draft
2. You create references between different parts of the draft tree
3. The referenced object is modified

The finalization process should handle these cross-references correctly and ensure all references point to the finalized (immutable) versions of the objects.

---
Repository: /testbed
