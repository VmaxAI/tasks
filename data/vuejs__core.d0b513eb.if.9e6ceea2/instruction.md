# Bug Report

### Describe the bug

When using a disabled Teleport component during SSR hydration, the component's anchor positioning is incorrect. This causes hydration mismatches and elements appearing in the wrong location after the client-side hydration completes.

### Reproduction

```vue
<template>
  <Teleport :disabled="true" to="#target">
    <div>Content that should stay in place</div>
  </Teleport>
  <div id="target"></div>
</template>
```

Steps to reproduce:
1. Server-render a page with a disabled Teleport component
2. Load the page in the browser and let Vue hydrate
3. The teleported content's position gets messed up during hydration

### Expected behavior

When a Teleport is disabled, the content should remain in its original position in the DOM tree during both SSR and hydration. The anchor nodes should be correctly identified so that subsequent updates work properly.

### System Info
- Vue version: 3.x
- SSR: Yes
- Node version: 18.x

---
Repository: /testbed
