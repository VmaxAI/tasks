# Bug Report

### Describe the bug

When using `defineProps` with TypeScript interface and providing default values via `withDefaults`, the generated runtime props are not being created correctly. The default values are not properly extracted from the props object, causing the component to fail at runtime.

### Reproduction

```vue
<script setup lang="ts">
interface Props {
  msg?: string
  count?: number
}

const props = withDefaults(defineProps<Props>(), {
  msg: 'hello',
  count: 0
})
</script>
```

When this component is compiled, the default values don't get properly assigned. The component either throws an error during compilation or the defaults are not applied at runtime.

### Expected behavior

The component should compile successfully and the default values should be properly applied to the props when they are not provided by the parent component.

### System Info
- Vue version: 3.x
- Using SFC with TypeScript

---
Repository: /testbed
