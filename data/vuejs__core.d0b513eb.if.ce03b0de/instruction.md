# Bug Report

### Describe the bug

I'm experiencing an issue with slot compilation in templates. When using named slots in components, the compiler seems to be incorrectly identifying which slot content belongs to which slot name. This causes the wrong slot content to be rendered or no content to be rendered at all.

### Reproduction

```vue
<template>
  <MyComponent>
    <template #header>
      <h1>Header Content</h1>
    </template>
    <template #footer>
      <p>Footer Content</p>
    </template>
  </MyComponent>
</template>
```

When this component is compiled and rendered, the named slots don't match up correctly. The header slot might show footer content or vice versa, or the slots might not render anything at all.

### Expected behavior

Named slots should correctly match their slot names and render the appropriate content in the correct slot positions. The `#header` template should render in the header slot and `#footer` should render in the footer slot.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

This seems to have started happening recently, possibly after a compiler update. The slot matching logic appears to be broken.

---
Repository: /testbed
