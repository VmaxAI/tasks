# Bug Report

### Describe the bug

When using props destructuring in `<script setup>`, the binding metadata is being set incorrectly. Props that are destructured with their original names (not aliased) are being treated as aliased props, and vice versa.

### Reproduction

```vue
<script setup>
const { foo, bar: baz } = defineProps(['foo', 'bar'])

// `foo` should be treated as a direct prop binding
// `baz` should be treated as an aliased prop binding (alias of `bar`)
// But the behavior is reversed
</script>
```

### Expected behavior

- When a prop is destructured with its original name (e.g., `foo`), it should be treated as a regular prop binding
- When a prop is destructured with an alias (e.g., `bar: baz`), it should be marked as `PROPS_ALIASED` in the binding metadata

Currently it seems like the logic is inverted - non-aliased props are being marked as aliased and aliased props are not being marked correctly.

### System Info
- Vue version: 3.x
- Using `<script setup>` with props destructuring enabled

---
Repository: /testbed
