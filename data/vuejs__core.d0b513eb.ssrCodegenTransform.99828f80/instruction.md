# Bug Report

### Describe the bug

I'm encountering an issue with SSR rendering where templates with multiple children are not being rendered correctly. It seems like the fragment detection logic is broken - templates that should be wrapped in fragments are not being wrapped, and vice versa.

Additionally, I'm seeing errors related to missing helper functions during SSR compilation. The generated code is trying to use helpers that aren't being included in the output.

### Reproduction

```vue
<template>
  <div>First child</div>
  <span>Second child</span>
</template>
```

When this component is server-side rendered, the output is incorrect. The multiple root nodes should be properly handled with fragment wrapping, but they're not.

Also noticed that some SSR helper imports are missing from the generated code, causing runtime errors during server rendering.

### Expected behavior

Templates with multiple root nodes should be correctly identified and wrapped in fragments during SSR compilation. All necessary SSR helper functions should be included in the compiled output.

### System Info
- Vue version: 3.x
- Node version: 18.x
- SSR mode

---
Repository: /testbed
