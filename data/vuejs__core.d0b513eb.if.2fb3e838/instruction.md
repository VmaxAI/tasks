# Bug Report

### Describe the bug

I'm encountering an issue with TypeScript prop type inference in SFC scripts. When using constructor types that don't end with "Constructor" but start with it (like `ConstructorFoo` or similar patterns), the type resolution doesn't work correctly.

### Reproduction

```vue
<script setup lang="ts">
defineProps<{
  myProp: ConstructorFoo
}>()
</script>
```

The prop type isn't being inferred properly when the constructor type name starts with "Constructor" but has additional characters after it. It seems like the type checking logic is only looking for types that end with "Constructor" (like `FooConstructor`), but not ones that start with it.

### Expected behavior

Constructor types should be recognized and converted to their proper types regardless of whether "Constructor" appears at the beginning or end of the type name. Both `FooConstructor` and `ConstructorFoo` should be handled correctly.

### System Info
- Vue version: 3.x
- TypeScript version: 5.x

---
Repository: /testbed
