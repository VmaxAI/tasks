# Bug Report

### Describe the bug

I'm experiencing an issue with `defineEmits` in SFC `<script setup>`. When defining emits using the type-only syntax with an empty object type, the compiler throws an error about mixing call signature with property syntax, even though no properties are actually defined.

### Reproduction

```vue
<script setup lang="ts">
// This should be valid but causes an error
const emit = defineEmits<{}>()

// Error: "defineEmits() type cannot mixed call signature and property syntax."
</script>
```

The same issue occurs with an interface:

```vue
<script setup lang="ts">
interface Emits {}

const emit = defineEmits<Emits>()
// Same error appears
</script>
```

### Expected behavior

An empty emits type definition should be valid and not throw an error. The component should compile successfully when no emits are needed but the type syntax is still used for consistency.

### System Info
- Vue version: 3.4.x
- Build tool: Vite

---
Repository: /testbed
