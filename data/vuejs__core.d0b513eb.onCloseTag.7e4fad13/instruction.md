# Bug Report

### Describe the bug

I'm experiencing an issue with template parsing where the inner location tracking for SFC (Single File Component) root elements seems to be incorrect. When I have a template with child elements, the `innerLoc.end` position is pointing to the wrong location - it appears to be using the start of the first child instead of the end of the last child.

### Reproduction

```vue
<template>
  <div>
    <span>First child</span>
    <span>Last child</span>
  </div>
</template>
```

When parsing this template, the `innerLoc.end` for the root `<div>` element should point to the position after "Last child", but it's pointing to the beginning of "First child" instead.

This is causing issues with source map generation and error reporting, as the reported locations don't match the actual positions in the source code.

### Expected behavior

The `innerLoc.end` should correctly point to the end position of the last child element in the SFC root tag, not the start position of the first child.

### Additional context

This seems to have broken recently and is affecting tooling that relies on accurate source locations for diagnostics and code transformation.

---
Repository: /testbed
