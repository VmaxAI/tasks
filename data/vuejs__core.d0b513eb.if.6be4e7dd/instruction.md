# Bug Report

### Describe the bug

After a recent update, reactive objects are completely broken. When trying to modify reactive state, the application crashes immediately with a syntax error. This appears to affect all reactive operations including simple property updates.

### Reproduction

```js
import { reactive } from 'vue'

const state = reactive({
  count: 0
})

// This causes the entire reactivity system to fail
state.count = 1
```

Even the most basic reactive operations fail now. The error occurs as soon as any property on a reactive object is modified.

### Expected behavior

Reactive property updates should work normally and trigger re-renders without causing syntax errors or crashes.

### System Info
- Vue version: 3.x
- Node version: 18.x

This is completely blocking our development. Any reactive state modification breaks the entire application.

---
Repository: /testbed
