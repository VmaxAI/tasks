# Bug Report

### Describe the bug

After a recent update, I'm getting runtime errors when working with Map and Set objects in Immer. The application crashes with an error about `assertUnrevoked` not being defined.

### Reproduction

```js
import {produce} from 'immer'

const state = {
  mySet: new Set([1, 2, 3])
}

// This throws an error
const nextState = produce(state, draft => {
  draft.mySet.add(4)
})
```

The error message says something like `assertUnrevoked is not a function` or `assertUnrevoked is not defined`.

### Expected behavior

Should be able to use Map and Set objects with produce without any errors. This was working fine before.

### System Info
- Immer version: latest
- Node version: 18.x

---
Repository: /testbed
