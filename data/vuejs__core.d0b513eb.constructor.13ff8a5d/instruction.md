# Bug Report

### Describe the bug

I'm encountering a critical issue where readonly reactive objects are completely broken. When trying to create a readonly reactive object, the application crashes immediately with a syntax error. This appears to be affecting all readonly reactive functionality.

### Reproduction

```js
import { readonly, reactive } from 'vue'

const original = reactive({
  count: 0,
  nested: {
    value: 'test'
  }
})

// This causes an immediate crash
const readonlyObj = readonly(original)
```

### Expected behavior

The `readonly()` function should create a readonly proxy of the reactive object without any errors. Attempts to modify the readonly object should be blocked (with warnings in dev mode), but reading values should work normally.

### System Info
- Vue version: 3.x
- Node version: 18.x

This is blocking our production deployment as we heavily rely on readonly for prop passing and state protection. Any help would be appreciated!

---
Repository: /testbed
