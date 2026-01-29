# Bug Report

### Describe the bug

I'm experiencing an issue with server-side rendering (SSR) hydration when inline styles are used. After hydration, the styles are not being applied correctly and I'm seeing hydration mismatch warnings in the console.

### Reproduction

```vue
<template>
  <div style="color: red; font-size: 14px; background: blue">
    Styled content
  </div>
</template>
```

When this component is server-rendered and then hydrated on the client, the styles don't match up properly. The element loses its styling after hydration completes.

### Expected behavior

The inline styles should be preserved during hydration and the element should maintain its appearance. No hydration mismatch warnings should appear.

### System Info
- Vue version: 3.x
- Node version: 18.x
- SSR framework: Nuxt/custom SSR setup

---
Repository: /testbed
