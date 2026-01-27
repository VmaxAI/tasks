# Bug Report

### Describe the bug

When using `app.onUnmount()` with an invalid argument (non-function), the expected warning is not being displayed. Instead, the warning appears when passing a valid function, which is the opposite of the intended behavior.

### Reproduction

```js
import { createApp } from 'vue'

const app = createApp({})

// This should trigger a warning but doesn't
app.onUnmount('not a function')
app.onUnmount(123)
app.onUnmount(null)

// This should NOT trigger a warning but does
app.onUnmount(() => {
  console.log('cleanup')
})
```

### Expected behavior

The warning should only be displayed when passing a non-function argument to `app.onUnmount()`. Valid function callbacks should be accepted without warnings.

### System Info
- Vue version: 3.x
- Environment: Development mode

---
Repository: /testbed
