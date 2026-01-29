# Bug Report

### Describe the bug

I'm encountering an issue with `<script setup>` where variables declared inside nested scopes (like if statements, loops, or block statements) are not being properly recognized. The compiler seems to be skipping over these nested declarations entirely.

### Reproduction

```vue
<script setup>
const outer = ref(1)

if (true) {
  const inner = ref(2)
  // inner should be accessible here
}

for (let i = 0; i < 5; i++) {
  const loopVar = ref(i)
  // loopVar should be scoped properly
}

{
  const blockScoped = ref(3)
  // blockScoped should be handled correctly
}
</script>

<template>
  <!-- These variables are not being processed correctly -->
  <div>{{ outer }}</div>
</template>
```

### Expected behavior

Variables declared in nested block scopes should be properly analyzed and handled by the compiler. The script setup compilation should traverse into all block statements and function scopes to correctly identify variable declarations.

### System Info

- Vue version: 3.x
- Node version: 18.x

This seems to have started happening recently. The compiler appears to be skipping over nested scopes when it shouldn't be.

---
Repository: /testbed
