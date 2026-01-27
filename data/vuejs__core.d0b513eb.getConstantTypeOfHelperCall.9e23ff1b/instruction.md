# Bug Report

### Describe the bug

I'm experiencing an issue where static content that should be hoisted is not being optimized correctly by the compiler. It seems like the compiler is treating certain helper function calls as non-constant even when they should be eligible for hoisting.

### Reproduction

```vue
<template>
  <div>
    <span :class="normalizeClass(['static-class'])">Test</span>
  </div>
</template>
```

When compiling this template, the `normalizeClass` call with a static array argument should be recognized as constant and eligible for hoisting, but it appears to be treated as a dynamic expression instead. This results in unnecessary re-evaluation during renders.

### Expected behavior

Helper calls like `normalizeClass`, `normalizeStyle`, and similar functions with constant arguments should be properly detected as hoistable static content. The compiler should recognize these patterns and optimize them accordingly.

### Additional context

This affects performance optimization as static content that could be hoisted outside the render function is being re-created on every render instead. The issue seems to be related to how the compiler determines constant types for helper function calls.

---
Repository: /testbed
