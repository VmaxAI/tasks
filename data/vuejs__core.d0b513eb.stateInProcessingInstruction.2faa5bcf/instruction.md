# Bug Report

### Describe the bug

Processing instructions in templates are not being parsed correctly. The closing `>` character appears to be included in the processing instruction content when it shouldn't be.

### Reproduction

```vue
<template>
  <?xml version="1.0"?>
  <div>Test</div>
</template>
```

When parsing templates with processing instructions (like XML declarations), the parser seems to include an extra character at the end of the processing instruction content. For example, `<?xml version="1.0"?>` is being parsed with the closing `>` as part of the instruction data.

### Expected behavior

Processing instructions should be parsed without including the closing delimiter in their content. The `>` character that closes the `?>` sequence should not be part of the instruction data itself.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

---
Repository: /testbed
