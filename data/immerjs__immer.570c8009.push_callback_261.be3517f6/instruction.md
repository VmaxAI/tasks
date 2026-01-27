# Bug Report

### Describe the bug

Something seems to be broken with draft creation in the latest version. When I try to create a draft object, I'm getting a syntax error that doesn't make any sense. The code was working fine before, but now it fails immediately when trying to initialize any draft state.

### Reproduction

```js
import {produce} from 'immer'

const baseState = {
  todos: [
    {id: 1, text: 'Buy milk', done: false},
    {id: 2, text: 'Walk dog', done: true}
  ]
}

// This throws an error now
const nextState = produce(baseState, draft => {
  draft.todos[0].done = true
})
```

### Expected behavior

The produce function should create a draft, allow modifications, and return the new immutable state without any errors. This was working perfectly in the previous version.

### System Info
- Immer version: latest
- Node version: 18.x
- Environment: Both browser and Node.js

This is blocking our entire development workflow. Any help would be appreciated!

---
Repository: /testbed
