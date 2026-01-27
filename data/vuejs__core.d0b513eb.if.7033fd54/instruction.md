# Bug Report

### Describe the bug

When using `<Teleport>` with a string selector for the `to` prop, the component fails to render to the target element. Instead of teleporting the content to the specified DOM selector, nothing is rendered and a warning appears in the console about the renderer not supporting string targets.

### Reproduction

```vue
<template>
  <Teleport to="#modal-container">
    <div class="modal">
      Modal content here
    </div>
  </Teleport>
</template>
```

```html
<!-- In index.html -->
<div id="modal-container"></div>
```

### Expected behavior

The modal content should be teleported to the `#modal-container` element in the DOM. The string selector should work as documented.

### Actual behavior

The content is not rendered and a console warning appears saying "Current renderer does not support string target for Teleports. (missing querySelector renderer option)" even though the renderer does support querySelector.

This seems to have broken recently as string selectors were working fine before. Using an actual DOM element reference works, but that's not always convenient.

---
Repository: /testbed
