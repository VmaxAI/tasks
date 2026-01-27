# Bug Report

### Describe the bug

I'm experiencing a critical issue where nested draft objects inside Sets and Maps are not being properly finalized. When I modify nested objects that are stored in a Set or Map, the changes don't persist correctly after the draft is finalized.

### Reproduction

```js
import { produce } from 'immer'

const state = {
  items: new Set([
    { id: 1, nested: { value: 'original' } }
  ])
}

const nextState = produce(state, draft => {
  const item = Array.from(draft.items)[0]
  item.nested.value = 'updated'
})

// The nested change is lost
console.log(Array.from(nextState.items)[0].nested.value)
// Expected: 'updated'
// Actual: 'original'
```

Similar issue occurs with Maps:

```js
const state = {
  data: new Map([
    ['key', { nested: { count: 0 } }]
  ])
}

const nextState = produce(state, draft => {
  draft.data.get('key').nested.count = 5
})

// Nested property change doesn't persist
console.log(nextState.data.get('key').nested.count)
// Expected: 5
// Actual: 0
```

### Expected behavior

Modifications to nested objects within Sets and Maps should be properly tracked and finalized, preserving all changes made during the draft phase.

### System Info
- immer version: latest
- Node version: 18.x

This is blocking our production deployment as we rely heavily on nested structures in collections. Any help would be appreciated!

---
Repository: /testbed
