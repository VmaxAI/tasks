# Bug Report

### Describe the bug

The `withDefaults` helper is showing runtime usage warnings in production builds when it should only warn during development. This causes unnecessary console output in production environments.

### Reproduction

```js
import { defineProps, withDefaults } from 'vue'

const props = withDefaults(defineProps<{
  msg?: string
  count?: number
}>(), {
  msg: 'hello',
  count: 0
})
```

When running this code in a production build, the console shows runtime usage warnings that should only appear in development mode.

### Expected behavior

Runtime usage warnings should only be displayed during development (`__DEV__` mode) and should be completely silent in production builds to avoid polluting the console.

### System Info
- Vue version: 3.x
- Build: Production

---
Repository: /testbed
