# Bug Report

### Describe the bug

I'm encountering an issue with the `srcset` attribute transformation in SFC templates. When using data URLs in a `srcset` attribute (which contain commas in their encoding), the compiler appears to be handling them incorrectly, leading to unexpected behavior or errors during template compilation.

### Reproduction

```vue
<template>
  <img srcset="data:image/png;base64,iVBORw0KGgo..., image2.png 2x" />
</template>
```

When the template compiler processes this, it seems to fail or produce incorrect output when dealing with data URLs that contain commas (which is standard for data URLs).

### Expected behavior

The compiler should correctly handle data URLs in `srcset` attributes, properly merging the comma-separated parts of the data URL and not treating the comma as a separator between image candidates.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-sfc

---
Repository: /testbed
