# Bug Report

### Describe the bug

When using the `@vue-ignore` comment directive with TypeScript types in SFC, the ignore behavior is not working as expected. The directive should allow ignoring type resolution for specific type definitions, but it seems to only work in certain cases.

### Reproduction

```vue
<script setup lang="ts">
// @vue-ignore
interface Props {
  foo: string
}

defineProps<Props>()
</script>
```

The `@vue-ignore` comment should prevent Vue from processing this type, but it's not being respected consistently. It appears that when there's only a single comment, the type is still being processed instead of being ignored.

### Expected behavior

When a type definition has a `@vue-ignore` comment, the compiler should skip processing that type and return empty props, regardless of how many comments are present.

### System Info
- Vue version: 3.x
- TypeScript version: 5.x

---
Repository: /testbed
