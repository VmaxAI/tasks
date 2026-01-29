# Bug Report

### Describe the bug

I'm experiencing an issue with template interpolation where whitespace at the end of the expression is not being handled correctly. The parser seems to be including trailing whitespace in the interpolation content when it should be trimmed.

### Reproduction

```vue
<template>
  <div>{{ message }}</div>
</template>
```

When the interpolation has trailing whitespace before the closing delimiter, the parsed expression includes that whitespace incorrectly. This affects the location information and potentially the expression content itself.

For example, with an interpolation like `{{ foo }}` where there's whitespace before `}}`, the parser doesn't properly trim the trailing space.

### Expected behavior

The parser should trim both leading and trailing whitespace from interpolation expressions, similar to how most template engines work. The expression content should not include any surrounding whitespace.

### System Info
- Vue version: 3.x
- Compiler: compiler-core

---
Repository: /testbed
