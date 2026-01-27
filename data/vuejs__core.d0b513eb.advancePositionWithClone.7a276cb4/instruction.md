# Bug Report

### Describe the bug

I'm experiencing an issue with template parsing where the position tracking seems to be incorrect when processing template content. The compiler appears to be calculating wrong offsets during parsing, which leads to incorrect error reporting and potentially broken source maps.

### Reproduction

```js
const template = `
<template>
  <div>{{ message }}</div>
</template>
`

// When the compiler processes this template, the position tracking
// for error messages and source maps is off
```

I noticed this when error messages started pointing to the wrong line/column positions in my templates. The issue seems to happen particularly when the compiler needs to advance through the entire source string.

### Expected behavior

The compiler should maintain accurate position information (offset, line, column) throughout the parsing process. Error messages should point to the correct location in the source template.

### System Info
- Vue version: 3.x
- Node version: 18.x

---
Repository: /testbed
