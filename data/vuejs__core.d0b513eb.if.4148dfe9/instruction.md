# Bug Report

### Describe the bug

I'm experiencing an issue with the `Omit` utility type when used in SFC type resolution. Properties that should be omitted from a type are still appearing in the resolved props, while properties that should be kept are being excluded.

### Reproduction

```vue
<script setup lang="ts">
interface User {
  id: number
  name: string
  email: string
  password: string
}

// Trying to omit 'password' from User
type SafeUser = Omit<User, 'password'>

defineProps<SafeUser>()
</script>
```

In this case, the `password` property is still accessible in the props, while `id`, `name`, and `email` are not available as expected.

### Expected behavior

When using `Omit<User, 'password'>`, the resulting type should include `id`, `name`, and `email` properties, but exclude the `password` property. The type resolution should correctly filter out the omitted keys and keep all other properties.

### System Info
- Vue version: 3.x
- Using TypeScript in SFC

---
Repository: /testbed
