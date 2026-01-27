# Bug Report

### Describe the bug

I'm experiencing a critical issue where nested draft objects inside Sets or Maps are not being properly finalized. When I have a Set or Map containing objects that themselves contain draft values, the nested drafts aren't being processed correctly during finalization.

### Reproduction

```js
import { produce } from 'immer'

const state = {
  items: new Set([
    { id: 1, nested: { value: 'test' } }
  ])
}

const nextState = produce(state, draft => {
  const item = Array.from(draft.items)[0]
  item.nested.value = 'updated'
})

// The nested draft isn't properly finalized
// Expected: Set containing object with finalized nested object
// Actual: Nested object may still be in draft state
```

Similar issue occurs with Maps:

```js
const state = {
  data: new Map([
    ['key1', { nested: { value: 'test' } }]
  ])
}

const nextState = produce(state, draft => {
  const item = draft.data.get('key1')
  item.nested.value = 'updated'
})
```

### Expected behavior

When finalizing a draft that contains Sets or Maps with nested draftable objects, all nested drafts should be properly processed and converted to their final immutable state. The cleanup callbacks should handle nested drafts within collection values.

### System Info
- Immer version: latest
- Node version: 18.x

This seems to have broken recently - nested drafts in collections used to work fine. Any help would be appreciated!

---
Repository: /testbed
