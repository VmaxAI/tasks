# Bug Report

### Describe the bug

After a recent update, I'm getting a syntax error when trying to use `Set` objects with Immer. The application fails to load and throws a parsing error related to the mapset plugin.

### Reproduction

```js
import { produce } from 'immer'
import { enableMapSet } from 'immer'

enableMapSet()

const state = {
  tags: new Set(['javascript', 'typescript'])
}

// This should work but causes the app to crash on load
const nextState = produce(state, draft => {
  draft.tags.add('react')
})
```

### Expected behavior

The code should execute without errors. Set operations should work normally after calling `enableMapSet()`.

### System Info
- Immer version: latest
- Node version: 18.x
- Browser: N/A (happens during build)

The error appears to be in the mapset plugin file itself - looks like there might be some invalid code that got introduced somehow. The app won't even start up now.

---
Repository: /testbed
