# Bug Report

### Describe the bug

After a recent update, I'm experiencing a complete application crash. When trying to use any reactive state operations, the app fails immediately with errors about missing functions. It seems like core proxy functionality has been completely broken.

### Reproduction

```js
import { produce } from 'immer'

const baseState = {
  items: [
    { id: 1, name: 'Item 1' },
    { id: 2, name: 'Item 2' }
  ]
}

// This crashes the application
const nextState = produce(baseState, draft => {
  draft.items[0].name = 'Updated Item'
})
```

### Expected behavior

The code should work as before and produce a new state with the updated item name. Instead, the application throws errors about undefined functions and fails to execute.

### System Info
- Immer version: latest
- Node version: 18.x
- Environment: Development

This is blocking our entire development workflow. Any help would be appreciated!

---
Repository: /testbed
