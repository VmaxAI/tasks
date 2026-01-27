# Bug Report

### Describe the bug

After a recent update, the reactivity system appears to be completely broken. When trying to use reactive objects or computed properties, I'm getting errors about undefined constructors and the application fails to initialize.

### Reproduction

```js
import { reactive, computed } from 'vue'

const state = reactive({
  count: 0
})

// Application crashes on initialization
const doubled = computed(() => state.count * 2)
```

### Expected behavior

The reactive state and computed properties should initialize normally without errors. The reactivity system should work as it did in previous versions.

### System Info
- Vue version: 3.x
- Node version: 18.x

Something seems to have gone wrong with the core reactivity implementation. The app won't even start up anymore.

---
Repository: /testbed
