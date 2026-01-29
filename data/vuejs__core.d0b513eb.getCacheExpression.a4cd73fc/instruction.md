# Bug Report

### Describe the bug

I'm encountering an issue with static node caching in the compiler. When using static content inside templates, the cached expressions are being duplicated unnecessarily, which affects the generated render function.

### Reproduction

```vue
<template>
  <div>
    <span>{{ staticText }}</span>
    <p>Some static content</p>
  </div>
</template>

<script setup>
const staticText = 'Hello World'
</script>
```

When compiling this template, the cache mechanism appears to be creating duplicate cache entries for the same static nodes. This results in the same value being cached twice instead of reusing the existing cached reference.

### Expected behavior

Static nodes should be cached once and reused efficiently. The compiler should generate a single cache entry per unique static value, not multiple entries for the same content.

### Additional context

This seems to affect the optimization of static content in the compiled output. The render function becomes less efficient due to redundant caching operations.

---
Repository: /testbed
