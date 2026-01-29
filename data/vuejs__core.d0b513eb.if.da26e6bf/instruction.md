# Bug Report

### Describe the bug

I'm experiencing an issue with Teleport components when using string selectors. After a recent update, teleports with string `to` props are not rendering correctly - the content just disappears instead of being teleported to the target element.

### Reproduction

```js
<template>
  <Teleport to="#modal-target">
    <div>This should be teleported</div>
  </Teleport>
</template>
```

When the component renders, the content inside the Teleport doesn't appear in the target element. Instead, nothing is rendered and I'm seeing a warning in the console about the renderer not supporting string targets, even though querySelector is available.

### Expected behavior

The content should be teleported to the element with id `modal-target`. This was working fine in previous versions.

### System Info
- Vue version: 3.x
- Browser: Chrome latest

This seems to have started happening after a recent update. The teleport just doesn't work with string selectors anymore, but it works fine when passing a DOM element directly.

---
Repository: /testbed
