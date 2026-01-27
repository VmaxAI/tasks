# Bug Report

### Describe the bug

When using `Exclude` utility type with string literal types in SFC `<script setup>` with TypeScript, the type resolution is not working correctly. Props or emits that use `Exclude` to filter out specific string literals are including the values that should be excluded instead of excluding them.

### Reproduction

```vue
<script setup lang="ts">
type AllColors = 'red' | 'blue' | 'green' | 'yellow'
type PrimaryColors = Exclude<AllColors, 'green' | 'yellow'>

// PrimaryColors should only allow 'red' | 'blue'
// but it's allowing 'green' | 'yellow' instead
defineProps<{
  color: PrimaryColors
}>()
</script>
```

Expected: `color` prop should only accept `'red'` or `'blue'`
Actual: `color` prop accepts `'green'` or `'yellow'` (the excluded values)

This affects any usage of the `Exclude` utility type in component props, emits, or other type definitions within SFC files. The behavior is inverted - excluded types are being kept while the types that should be kept are being excluded.

### System Info
- Vue version: 3.x
- TypeScript: latest

---
Repository: /testbed
