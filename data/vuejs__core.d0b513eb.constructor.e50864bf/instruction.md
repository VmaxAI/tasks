# Bug Report

### Describe the bug

After updating to the latest version, I'm getting a syntax error when trying to use `reactive()` or any reactivity features. The application fails to load and throws an error about unexpected token/syntax.

### Reproduction

```js
import { reactive } from 'vue'

const state = reactive({
  count: 0
})

// Application crashes on load before even reaching this point
```

### Expected behavior

The reactive state should be created successfully and the application should load without errors.

### System Info
- Vue version: 3.x (latest)
- Node version: 18.x
- Build tool: Vite

This seems to have started after the most recent update. Rolling back to the previous version fixes the issue. Not sure what changed but something in the reactivity handlers appears to be broken.

---
Repository: /testbed
