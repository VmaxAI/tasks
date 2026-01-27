# Bug Report

### Describe the bug

I'm experiencing an issue with TypeScript union type resolution in SFC (Single File Component) compiler. When using union types with type references, the compiler seems to fail to properly resolve the referenced types, leading to incorrect type inference.

### Reproduction

```vue
<script setup lang="ts">
type Status = 'active' | 'inactive'
type User = { name: string; status: Status }

type Result = User | null

// Type resolution doesn't work correctly here
const result: Result = { name: 'John', status: 'active' }
</script>
```

When the compiler tries to resolve the `Result` union type that includes a type reference (`User`), it doesn't properly expand the referenced type. This causes issues with type checking and intellisense in the template.

### Expected behavior

The compiler should correctly resolve type references within union types, so that `Result` is properly understood as `{ name: string; status: Status } | null`.

### System Info
- Vue version: 3.x
- TypeScript: 5.x

---
Repository: /testbed
