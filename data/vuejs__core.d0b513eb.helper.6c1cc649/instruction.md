# Bug Report

### Describe the bug

I'm encountering an issue with block tracking in generated render functions. When `disableTracking` is set, the generated code appears to be inverted - it's passing `true` to `openBlock()` when tracking should be enabled, and passing nothing when it should be disabled.

This is causing unexpected behavior in components where block tracking needs to be explicitly disabled (like in certain optimization scenarios). The rendered output is working, but the tracking behavior is backwards from what's expected.

### Reproduction

```js
// Template that should have tracking disabled
const template = `<div v-if="show"><span>test</span></div>`

// When compiling with disableTracking option
const { code } = compile(template, {
  hoistStatic: true,
  // ... other options that trigger disableTracking
})

// The generated openBlock call has inverted logic
// Expected: openBlock() when tracking disabled
// Actual: openBlock(true) when tracking disabled
```

### Expected behavior

When `disableTracking` is true, `openBlock()` should be called without arguments. When `disableTracking` is false, `openBlock(true)` should be called with the `true` argument.

The current behavior seems to have the boolean logic reversed.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

---
Repository: /testbed
