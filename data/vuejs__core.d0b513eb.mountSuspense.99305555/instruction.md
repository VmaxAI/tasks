# Bug Report

### Describe the bug

I'm experiencing an issue with `<Suspense>` where the content is being rendered directly into the container instead of an off-DOM container during the initial mount. This causes the async content to flash briefly before the fallback is shown, which creates a jarring user experience.

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

When the `AsyncComponent` has async dependencies, I can see the actual content flash on screen for a split second before the loading fallback appears. This shouldn't happen - the fallback should be shown immediately while the async content is being resolved off-screen.

### Expected behavior

The async content should be mounted in an off-DOM container first, so it's never visible to the user until it's fully resolved. Only the fallback should be visible during the loading phase.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox (happens in both)

This seems like a regression as I don't remember seeing this behavior in earlier versions. The content flashing before the fallback makes the loading state look broken.

---
Repository: /testbed
