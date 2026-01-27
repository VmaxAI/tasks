# Bug Report

### Describe the bug

I'm experiencing an issue with SSR component rendering where slot content is not being rendered correctly. It seems like the first slot in a component with multiple slots is being skipped during server-side rendering.

### Reproduction

```js
// Component with multiple named slots
<template>
  <MyComponent>
    <template #header>
      <h1>Header Content</h1>
    </template>
    <template #body>
      <p>Body Content</p>
    </template>
    <template #footer>
      <span>Footer Content</span>
    </template>
  </MyComponent>
</template>
```

When rendering this component on the server, the header slot content is missing from the output, but the body and footer slots render correctly.

### Expected behavior

All slot content should be rendered in the SSR output, including the first slot. The rendered HTML should include the header, body, and footer content.

### System Info

- Vue version: 3.x
- SSR: Yes
- Node version: 18.x

This seems to have started happening recently. The client-side hydration works fine, but the initial SSR output is missing the first slot's content.

---
Repository: /testbed
