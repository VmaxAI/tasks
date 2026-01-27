# Bug Report

### Describe the bug

I'm experiencing an issue where the template parser seems to be cutting off or not properly handling attribute values in certain cases. When parsing templates with attributes, especially directives with modifiers, the parsing appears to be incomplete or truncated.

### Reproduction

```vue
<template>
  <div v-bind:foo.sync="bar"></div>
</template>
```

When trying to parse templates with directives that have modifiers (like `.sync` in the v-bind example above), the parser doesn't seem to complete processing the attribute properly. The issue appears to affect how attribute values are finalized and how directive modifiers are handled.

### Expected behavior

The parser should correctly process and finalize all attributes and directives, including their modifiers, without truncation or incomplete processing. All attribute metadata (name, value, modifiers) should be properly captured and stored.

### System Info
- Vue version: 3.x
- Compiler: compiler-core

This seems to have started happening recently and affects template compilation. Any help would be appreciated!

---
Repository: /testbed
