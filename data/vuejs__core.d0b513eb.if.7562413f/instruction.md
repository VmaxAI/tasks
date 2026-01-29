# Bug Report

### Describe the bug

I'm encountering an issue with `defineProps()` in SFC `<script setup>` where the compiler is not properly validating when both type parameters and runtime arguments are provided simultaneously. The error message that should prevent mixing these two approaches is being triggered in the wrong scenario.

### Reproduction

```vue
<script setup lang="ts">
// This should throw an error but doesn't
const props = defineProps<{ msg: string }>({ msg: String })
</script>
```

The above code mixes type-based props declaration (using TypeScript generics) with runtime props declaration (using an object argument), which should not be allowed.

### Expected behavior

The compiler should throw an error: `defineProps() cannot accept both type and non-type arguments at the same time. Use one or the other.`

Instead, it seems like the validation logic is inverted - the error is being shown in cases where it shouldn't be, or not being shown when it should be.

### System Info
- Vue version: 3.x
- Using `<script setup>` with TypeScript

---
Repository: /testbed
