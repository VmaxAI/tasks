# Bug Report

### Describe the bug

I'm experiencing a critical issue where cross-references between draft objects are not being handled correctly. When I have nested drafts that reference each other, the finalization process seems to break and the references don't get updated properly.

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

// Set up a cross-reference
baseState.selectedItem = baseState.items[0]

const nextState = produce(baseState, draft => {
  // Modify the referenced item
  draft.items[0].name = 'Updated Item'
})

// The cross-reference should be updated but it's not working
console.log(nextState.selectedItem.name) // Expected: 'Updated Item', but behavior is broken
```

### Expected behavior

When objects contain cross-references to other parts of the draft tree within the same scope, those references should be properly updated during finalization. The callback that handles updating the parent with the finalized value should be registered and executed.

### Additional context

This seems to affect any scenario where:
1. You have nested objects in a draft
2. One object references another object in the same draft scope
3. The referenced object gets modified

The finalization logic appears to be completely broken for these cross-reference scenarios. Without proper callback registration, the parent objects never get updated with the finalized values.

---
Repository: /testbed
