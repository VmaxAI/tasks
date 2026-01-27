# Bug Report

### Describe the bug

I'm experiencing an issue with static prop hoisting in the compiler. It seems like the first property in an object is being skipped during constant type evaluation, which leads to incorrect hoisting behavior.

### Reproduction

```vue
<template>
  <div :class="{ active: true, disabled: false }" />
</template>
```

When compiling this template, the props object isn't being correctly analyzed. The first property (`active: true`) appears to be ignored during the constant type check, which affects whether the entire props object can be hoisted as a static constant.

This also affects other scenarios where multiple props are defined:

```vue
<template>
  <Component :foo="'bar'" :baz="'qux'" />
</template>
```

### Expected behavior

All properties in the props object should be evaluated to determine if they can be hoisted as constants. The first property shouldn't be skipped during the analysis.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

---
Repository: /testbed
