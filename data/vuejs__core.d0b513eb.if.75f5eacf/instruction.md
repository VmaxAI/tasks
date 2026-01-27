# Bug Report

### Describe the bug

I'm experiencing an issue with destructured props in `<script setup>` where variables from destructured `defineProps()` are not being properly recognized as props, causing reactivity issues. It seems like destructured prop identifiers are being treated as local variables instead of prop references.

### Reproduction

```vue
<script setup>
const { foo, bar } = defineProps({
  foo: String,
  bar: Number
})

// These should be reactive prop references
// but they're being treated as regular variables
console.log(foo, bar)
</script>
```

When using destructured props like this, the compiler doesn't seem to handle them correctly. The props lose their reactive connection and behave like plain local variables.

### Expected behavior

Destructured props from `defineProps()` should maintain their reactivity and be properly recognized as props by the compiler, not treated as excluded local bindings.

### System Info
- Vue version: 3.x
- Using `<script setup>` with TypeScript

This might be related to how the compiler tracks prop identifiers during the transformation phase. Any help would be appreciated!

---
Repository: /testbed
