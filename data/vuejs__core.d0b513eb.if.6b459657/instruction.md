# Bug Report

### Describe the bug

After a recent update, reactive objects are not triggering updates when properties are modified. When I set a property on a reactive object, the UI doesn't re-render and computed values that depend on that property don't recalculate.

### Reproduction

```js
const state = reactive({
  count: 0,
  message: 'hello'
})

// This change doesn't trigger any updates
state.count = 5

// Computed values don't update either
const doubled = computed(() => state.count * 2)
console.log(doubled.value) // Still shows 0 instead of 10
```

### Expected behavior

Setting properties on reactive objects should trigger reactivity updates. Any components or computed values that depend on the changed property should update accordingly.

### Additional context

This seems to affect all SET operations on reactive objects. Adding new properties (ADD) and deleting properties (DELETE) also don't seem to trigger updates. The reactivity system appears to be completely broken for property modifications.

---
Repository: /testbed
