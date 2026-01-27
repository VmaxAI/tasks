# Bug Report

### Describe the bug

When using `<Teleport>` with the `disabled` prop during SSR hydration, the component fails to hydrate correctly. The teleported content gets misaligned and the anchor nodes are set incorrectly, causing hydration mismatches.

### Reproduction

```vue
<template>
  <div>
    <Teleport :disabled="true" to="#target">
      <div>Content that should stay in place</div>
    </Teleport>
    <div id="target"></div>
  </div>
</template>
```

Steps to reproduce:
1. Set up SSR with a Teleport component
2. Use the `disabled` prop set to `true`
3. Render on server and hydrate on client
4. Observe hydration warnings/errors

The teleported content doesn't hydrate properly when the teleport is disabled. It seems like the anchor positions are being calculated incorrectly during the hydration phase.

### Expected behavior

When a Teleport is disabled during hydration, it should hydrate the children in their current location (where they were server-rendered) without attempting to move them to the target element. The anchor nodes should point to the correct DOM positions.

### System Info
- Vue version: 3.x
- Node version: 18.x
- SSR: Yes

---
Repository: /testbed
