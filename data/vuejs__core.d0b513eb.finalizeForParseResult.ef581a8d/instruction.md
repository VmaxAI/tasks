# Bug Report

### Describe the bug

I'm experiencing an issue with v-for directives where the compiler seems to be validating the wrong expressions. When using v-for with index and value parameters, the validation appears to be swapped - it's checking the index expression when it should check the value, and vice versa.

### Reproduction

```vue
<template>
  <div v-for="(item, index) in items" :key="index">
    {{ item }} - {{ index }}
  </div>
</template>
```

When the compiler processes this, it seems to validate the wrong parts of the v-for expression. This causes issues with browser expression validation in certain edge cases, particularly when using complex expressions or destructuring patterns.

### Expected behavior

The compiler should correctly validate:
- The `value` expression (item) as the value
- The `index` expression (index) as the index

Not the other way around.

### Additional context

This might be related to recent changes in the compiler's v-for transform logic. The issue is subtle and might not be immediately apparent in simple cases, but it can cause problems with more complex v-for patterns or when using strict validation modes.

---
Repository: /testbed
