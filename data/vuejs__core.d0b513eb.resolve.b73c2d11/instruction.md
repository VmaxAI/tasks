# Bug Report

### Describe the bug

The `Suspense` component appears to be broken after a recent change. When using Suspense boundaries in my application, the component fails to resolve properly and the pending content never gets mounted to the DOM.

### Reproduction

```vue
<template>
  <Suspense>
    <template #default>
      <AsyncComponent />
    </template>
    <template #fallback>
      <div>Loading...</div>
    </template>
  </Suspense>
</template>
```

When the async component finishes loading, the suspense boundary doesn't transition from the fallback to the actual content. The fallback just stays visible indefinitely.

### Expected behavior

The Suspense component should:
1. Show the fallback content while async components are loading
2. Automatically transition to show the resolved content once loading completes
3. Properly unmount the fallback and mount the default slot content

### System Info

- Vue version: 3.x
- Build tool: Vite

This seems like it might be related to the resolve logic in the Suspense implementation. The component worked fine in previous versions but stopped working recently.

---
Repository: /testbed
