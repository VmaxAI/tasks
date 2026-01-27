# Bug Report

### Describe the bug

I'm experiencing an issue with reactive arrays where calling `.entries()` on a reactive array returns entries with the raw values instead of reactive proxies. The second element of each entry tuple should be wrapped in a reactive proxy but it's not happening.

### Reproduction

```js
import { reactive } from 'vue'

const arr = reactive([{ name: 'item1' }, { name: 'item2' }])

for (const [index, item] of arr.entries()) {
  console.log(item)
  // Expected: Proxy object (reactive)
  // Actual: Raw object (not reactive)
  
  // Modifying the item doesn't trigger reactivity
  item.name = 'updated'
}
```

### Expected behavior

When iterating over a reactive array using `.entries()`, the values in the returned tuples should be reactive proxies (wrapped with `toReactive()`), similar to how other array iterator methods work. This would ensure that any modifications to nested objects maintain reactivity.

### System Info
- Vue version: 3.x
- Using reactive arrays with nested objects

---
Repository: /testbed
