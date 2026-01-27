# Bug Report

### Describe the bug

When using TypeScript type references with the `Array` generic type in SFC script setup, the compiler seems to have issues resolving array element types in certain cases. Specifically, when working with empty or improperly formatted Array type parameters, the type resolution doesn't work as expected.

### Reproduction

```vue
<script setup lang="ts">
interface Item {
  id: number
  name: string
}

// This causes issues with type resolution
const items: Array<Item> = []

// Type information is not properly extracted
defineProps<{
  data: Array<Item>
}>()
</script>
```

The compiler should be able to resolve the element type from `Array<Item>` syntax, but it appears to fail in certain scenarios, particularly when the Array type reference is used in props definitions or when combined with other type operations.

### Expected behavior

The compiler should correctly resolve `Array<Item>` to extract `Item` as the element type, regardless of how the Array type is used within the SFC.

### System Info
- Vue version: 3.x
- TypeScript: 5.x

---
Repository: /testbed
