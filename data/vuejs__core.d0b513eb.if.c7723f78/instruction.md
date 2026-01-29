# Bug Report

### Describe the bug

I'm experiencing an issue with TypeScript array type resolution in SFC scripts. When using array types in props or other type definitions, the compiler seems to be handling the array element type incorrectly, which leads to unexpected behavior during type checking.

### Reproduction

```vue
<script setup lang="ts">
interface Props {
  items: string[]
}

const props = defineProps<Props>()

// Type resolution for the array doesn't work as expected
// The element type should be properly extracted
</script>
```

When the compiler tries to resolve the `string[]` type, it appears to be returning the wrong structure for the element type. This affects type inference and validation in components that use array types.

### Expected behavior

Array types like `string[]`, `number[]`, etc. should have their element types properly extracted and returned as an array containing the element type node. The type resolution should correctly identify that `string[]` has an element type of `string`.

### System Info
- Vue version: 3.x
- TypeScript: latest

This seems to have broken recently and is affecting prop type validation in my components. Any help would be appreciated!

---
Repository: /testbed
