# Bug Report

### Describe the bug

I'm experiencing an issue with template parsing where attribute values enclosed in double quotes are not being parsed correctly. The first character of the attribute value appears to be missing or incorrectly handled.

### Reproduction

```vue
<template>
  <div title="Hello"></div>
</template>
```

When parsing this template, the attribute value seems to be off by one character. For example, an attribute like `title="Hello"` might be parsed as `ello` instead of `Hello`.

### Expected behavior

Attribute values with double quotes should be parsed completely, including the first character. The parsed value should match exactly what's between the quotes.

### System Info
- Vue version: 3.x
- Node version: 18.x

This seems to affect only double-quoted attributes - single-quoted attributes and unquoted attributes appear to work fine.

---
Repository: /testbed
