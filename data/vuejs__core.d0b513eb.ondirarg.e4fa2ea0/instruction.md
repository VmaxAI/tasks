# Bug Report

### Describe the bug

I'm experiencing an issue with directive arguments in templates when using `v-pre`. The directive argument seems to be incorrectly parsed - it includes an extra character at the beginning that shouldn't be there.

### Reproduction

```vue
<template>
  <div v-pre>
    <button v-on:click="handler">Click me</button>
  </div>
</template>
```

When parsing the template above, the directive argument (`:click`) is not being handled correctly within the `v-pre` block. The attribute name ends up including characters it shouldn't.

### Expected behavior

The directive argument should be properly extracted and added to the attribute name without any extra characters. The parser should correctly handle the colon-prefixed argument syntax even within `v-pre` blocks.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

---
Repository: /testbed
