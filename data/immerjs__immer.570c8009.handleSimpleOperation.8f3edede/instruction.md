# Bug Report

### Describe the bug

After a recent update, array mutation methods like `push`, `pop`, `shift`, `unshift`, `splice`, etc. are completely broken and throw errors when called on draft arrays. The application crashes whenever I try to use these methods.

### Reproduction

```js
import { produce } from 'immer'

const state = {
  items: [1, 2, 3]
}

const nextState = produce(state, draft => {
  draft.items.push(4)  // This throws an error
})
```

Also happens with other array methods:

```js
produce(state, draft => {
  draft.items.pop()      // Error
  draft.items.shift()    // Error
  draft.items.unshift(0) // Error
  draft.items.splice(1, 1) // Error
})
```

### Expected behavior

Array methods should work normally on draft arrays and produce the expected mutations. The code above should successfully add/remove elements from the array without throwing errors.

### Additional context

This was working fine in the previous version. It seems like something fundamental broke with array method handling. The error suggests that the method implementation is missing or corrupted.

---
Repository: /testbed
