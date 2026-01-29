# Bug Report

### Describe the bug

I'm experiencing an issue with identifier tracking in the compiler. When the same identifier is used multiple times in a template, the reference count seems to be incorrect. This causes problems with scope analysis and can lead to incorrect code generation.

### Reproduction

```js
// Template with repeated identifier usage
const template = `
  <div v-for="item in items">
    {{ item }}
    <span v-if="item">{{ item }}</span>
  </div>
`

// The identifier 'item' appears multiple times but the tracking
// doesn't increment properly after the first occurrence
```

### Expected behavior

The compiler should correctly track how many times an identifier is referenced within a scope. Each usage of the same identifier should increment the reference count, allowing the compiler to properly determine variable scope and optimize code generation.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

---
Repository: /testbed
