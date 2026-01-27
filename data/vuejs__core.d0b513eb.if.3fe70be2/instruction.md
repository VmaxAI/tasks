# Bug Report

### Describe the bug

I'm experiencing an issue with `defineProps()` type validation in SFC `<script setup>`. When I try to use `defineProps()` with both runtime props declaration and type parameters at the same time, the compiler doesn't throw an error as expected. Instead, it allows the invalid syntax to pass through.

### Reproduction

```vue
<script setup lang="ts">
interface Props {
  msg: string
}

// This should throw a compilation error but doesn't
const props = defineProps<Props>({
  msg: String
})
</script>
```

### Expected behavior

The compiler should throw an error stating that `defineProps()` cannot accept both type and non-type arguments at the same time. You should only be able to use one approach:

**Either runtime declaration:**
```js
const props = defineProps({
  msg: String
})
```

**Or type-based declaration:**
```js
const props = defineProps<Props>()
```

But not both together. The current behavior allows this invalid syntax to compile without any warnings.

### System Info
- Vue version: 3.x
- Using SFC with TypeScript

---
Repository: /testbed
