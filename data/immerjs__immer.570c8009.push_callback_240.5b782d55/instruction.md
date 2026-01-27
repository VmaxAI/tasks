# Bug Report

### Describe the bug

After a recent update, I'm experiencing unexpected behavior when working with nested draft objects in Sets and Maps. It seems like nested drafts inside non-draft values are not being properly handled during finalization.

### Reproduction

```js
import { produce } from 'immer'

const state = {
  mySet: new Set([{ nested: { value: 1 } }])
}

const nextState = produce(state, draft => {
  const item = Array.from(draft.mySet)[0]
  item.nested.value = 2
})

// The nested draft changes are not being processed correctly
console.log(Array.from(nextState.mySet)[0].nested.value)
// Expected: 2
// Actual: behavior is inconsistent
```

Similar issue occurs with Maps:

```js
const state = {
  myMap: new Map([['key', { nested: { value: 1 } }]])
}

const nextState = produce(state, draft => {
  draft.myMap.get('key').nested.value = 2
})
```

### Expected behavior

When modifying nested properties within objects stored in Sets or Maps, those changes should be properly finalized and reflected in the produced state.

### System Info
- immer version: latest
- Node version: 18.x

This seems to have broken after the latest changes. The finalization logic appears to be missing some cleanup callbacks for handling nested drafts in collection types.

---
Repository: /testbed
