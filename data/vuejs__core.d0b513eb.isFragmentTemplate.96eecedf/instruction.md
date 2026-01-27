# Bug Report

### Describe the bug

I'm experiencing an issue with template parsing where `<template>` tags with structural directives like `v-if`, `v-for`, etc. are being treated incorrectly. The compiler seems to have inverted logic when determining whether a template should be treated as a fragment.

### Reproduction

```vue
<template>
  <div>
    <template v-if="show">
      <p>Content</p>
    </template>
  </div>
</template>
```

When compiling this template, the `<template v-if>` block is not being handled as expected. It appears the compiler is incorrectly identifying which templates should be treated as fragments vs regular elements.

### Expected behavior

Templates with structural directives (`v-if`, `v-else`, `v-else-if`, `v-for`, `v-slot`) should be recognized and processed as fragment templates. Regular `<template>` tags without these directives should be handled differently.

The current behavior seems backwards - templates that should be fragments aren't being treated as such, and vice versa.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

This is causing issues with conditional rendering and list rendering when using template wrappers. Any template with structural directives is being misidentified.

---
Repository: /testbed
