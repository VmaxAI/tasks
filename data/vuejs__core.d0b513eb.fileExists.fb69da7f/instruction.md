# Bug Report

### Describe the bug

I'm experiencing an issue with TypeScript type resolution in SFC files. When importing types from `.vue` files, the compiler fails to resolve them correctly in certain cases.

### Reproduction

```vue
<!-- MyComponent.vue -->
<script setup lang="ts">
export interface MyProps {
  value: string
}
</script>

<!-- AnotherComponent.vue -->
<script setup lang="ts">
import type { MyProps } from './MyComponent.vue'

// Type resolution fails here
const props: MyProps = { value: 'test' }
</script>
```

The type import doesn't work as expected and the compiler can't find the type definition from the `.vue` file.

### Expected behavior

The compiler should correctly resolve type imports from `.vue` files and the type checking should work without errors.

### System Info
- Vue version: 3.x
- TypeScript version: 5.x

This seems to have started happening recently. The type resolution was working fine before.

---
Repository: /testbed
