# Bug Report

### Describe the bug

After a recent update, I'm getting a runtime error when trying to use Immer with any objects or arrays. The library seems to have completely broken - it's throwing errors about `isDraftable` not being a function.

### Reproduction

```js
import produce from 'immer'

const state = {
  users: ['Alice', 'Bob'],
  count: 0
}

// This throws an error
const nextState = produce(state, draft => {
  draft.count += 1
})
```

### Expected behavior

The code should work normally and create a new immutable state with the updated count. This was working fine before.

### System Info
- Immer version: latest
- Node version: 18.x
- Environment: Both browser and Node.js

---
Repository: /testbed
