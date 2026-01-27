# Bug Report

### Describe the bug

I'm getting a syntax error when using the `.sync` modifier with `v-bind` in compatibility mode. The compiler is crashing instead of showing the proper deprecation warning message.

### Reproduction

```vue
<template>
  <MyComponent v-bind:title.sync="pageTitle" />
</template>
```

When compiling this template with compatibility mode enabled, I get an error instead of the expected deprecation warning.

### Expected behavior

The compiler should display a deprecation message explaining that `.sync` has been removed and suggesting to use `v-model:title` instead, similar to other compatibility warnings.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

---
Repository: /testbed
