# Bug Report

### Describe the bug

I'm experiencing an issue with computed properties that depend on other computed properties. When the dependency chain updates, the dependent computed values don't always refresh correctly. It seems like some intermediate computed values are being skipped during the dirty check process.

### Reproduction

```js
import { ref, computed, effect } from 'vue'

const count = ref(0)
const double = computed(() => count.value * 2)
const quadruple = computed(() => double.value * 2)

effect(() => {
  console.log('quadruple:', quadruple.value)
})

count.value = 1
// Expected: quadruple should be 4
// Actual: quadruple may not update or show incorrect value
```

### Expected behavior

When `count` changes, both `double` and `quadruple` should update properly. The effect should log the correct computed value each time.

### System Info
- Vue version: 3.x
- Node: 18.x

---
Repository: /testbed
