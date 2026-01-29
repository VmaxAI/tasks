# Bug Report

### Describe the bug

When using slots with fallback content in SSR, the fallback content is not rendering correctly in certain cases. It seems like the logic for detecting empty slots is not working as expected, causing fallback content to be shown when it shouldn't be or vice versa.

### Reproduction

```vue
<template>
  <MyComponent>
    <template #default>
      <!-- slot content here -->
    </template>
  </MyComponent>
</template>

<script setup>
// Component with fallback slot content
</script>
```

When rendering this component on the server, the slot detection appears to be broken. The fallback content behavior is inconsistent with what happens in client-side rendering.

### Expected behavior

The SSR output should correctly detect whether a slot has content or not, and only render fallback content when the slot is truly empty. This should match the behavior of client-side rendering.

### System Info
- Vue version: 3.x
- Environment: Server-side rendering

---
Repository: /testbed
