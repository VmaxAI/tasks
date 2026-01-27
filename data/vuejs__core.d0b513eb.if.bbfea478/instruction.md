# Bug Report

### Describe the bug

I'm experiencing an issue with TypeScript prop type inference in SFC `<script setup>`. When using object syntax for props with the `required` field, the optional/required state seems to be inverted.

### Reproduction

```vue
<script setup lang="ts">
defineProps<{
  myProp: {
    type: String
    required: true
  }
}>()
</script>
```

When I use `required: true` in the prop definition, the prop is being treated as optional. Conversely, when I set `required: false` or omit it entirely, the prop becomes required.

This is causing type checking issues where:
- Props marked as `required: true` don't throw errors when omitted from parent components
- Props marked as `required: false` throw errors when they're not provided

### Expected behavior

Props with `required: true` should be treated as required (not optional), and props with `required: false` or without the `required` field should be treated as optional.

### System Info
- Vue version: 3.x
- TypeScript version: 5.x

---
Repository: /testbed
