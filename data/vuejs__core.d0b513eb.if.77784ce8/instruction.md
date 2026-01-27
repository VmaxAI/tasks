# Bug Report

### Describe the bug

I'm encountering an issue with `v-if` directives when they don't have an expression. It seems like the compiler is not properly validating or handling missing expressions for `v-if` and `v-else-if` directives.

### Reproduction

```vue
<template>
  <div v-if>This should show an error</div>
  <div v-else-if>This should also show an error</div>
</template>
```

When compiling templates with `v-if` or `v-else-if` without expressions, the compiler doesn't generate the expected error. The directives are being treated as if they have valid expressions.

### Expected behavior

The compiler should throw an error when `v-if` or `v-else-if` directives are used without an expression. Only `v-else` should be allowed without an expression since it doesn't need a condition.

For example:
```vue
<div v-if="condition">Valid</div>
<div v-else-if="otherCondition">Valid</div>
<div v-else>Valid - no expression needed</div>

<div v-if>Invalid - should error</div>
<div v-else-if>Invalid - should error</div>
```

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

---
Repository: /testbed
