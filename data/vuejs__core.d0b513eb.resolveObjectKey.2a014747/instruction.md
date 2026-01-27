# Bug Report

### Describe the bug

I'm experiencing issues with object key resolution in SFC script setup. When using computed property names or numeric keys in object literals, the compiler is not handling them correctly.

### Reproduction

```vue
<script setup>
const obj = {
  [computedKey]: 'value1',
  123: 'value2',
  regularKey: 'value3'
}
</script>
```

When compiling the above code:
- Computed property names (like `[computedKey]`) are being treated as regular identifiers
- Numeric keys (like `123`) are returning the wrong type instead of being converted to strings
- Regular non-computed identifiers are being ignored when they should be recognized

### Expected behavior

The compiler should correctly:
1. Recognize computed property names and handle them appropriately
2. Convert numeric keys to their string representation
3. Process regular identifier keys when not in computed context

### System Info
- Vue version: 3.x
- Using SFC with script setup

---
Repository: /testbed
