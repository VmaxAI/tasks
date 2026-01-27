# Bug Report

### Describe the bug

I'm experiencing an issue with structural directives in templates. When a structural directive (like `v-if`, `v-for`, etc.) is the first directive on an element, it seems to be completely ignored during template compilation. The directive doesn't get processed and the resulting output is incorrect.

### Reproduction

```vue
<template>
  <div v-if="show" class="content">
    Hello World
  </div>
</template>
```

When `v-if` is the first prop/directive on the element, it's not being transformed properly. However, if I add another attribute before it, it works:

```vue
<template>
  <!-- This works -->
  <div class="content" v-if="show">
    Hello World
  </div>
</template>
```

The issue appears to affect all structural directives when they're in the first position.

### Expected behavior

Structural directives should be processed regardless of their position in the props array. The order of attributes/directives shouldn't matter for correct compilation.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

---
Repository: /testbed
