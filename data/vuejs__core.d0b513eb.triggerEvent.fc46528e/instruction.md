# Bug Report

### Describe the bug

The `onResolve`, `onPending`, and `onFallback` event handlers on Suspense components are not being triggered. When these events should fire, nothing happens and the callbacks are not executed.

### Reproduction

```vue
<template>
  <Suspense @onResolve="handleResolve" @onPending="handlePending">
    <AsyncComponent />
  </Suspense>
</template>

<script setup>
const handleResolve = () => {
  console.log('Suspense resolved')
}

const handlePending = () => {
  console.log('Suspense pending')
}
</script>
```

When the async component loads or enters pending state, the event handlers are not called. The console logs never appear even though the Suspense component is working otherwise (showing fallback content, etc).

### Expected behavior

The event handlers should be invoked when the corresponding Suspense events occur. `onResolve` should fire when async content resolves, `onPending` when entering pending state, and `onFallback` when showing fallback content.

### System Info
- Vue version: 3.x
- Runtime: Browser

---
Repository: /testbed
