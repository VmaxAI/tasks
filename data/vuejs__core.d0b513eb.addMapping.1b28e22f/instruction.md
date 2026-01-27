# Bug Report

### Describe the bug

Source maps are generating incorrect column mappings when compiling templates. The generated source map points to wrong positions in the original source code, making debugging extremely difficult.

### Reproduction

```js
// Compile a template with source map enabled
const { code, map } = compile('<div>{{ message }}</div>', {
  sourceMap: true,
  filename: 'test.vue'
})

// Check the source map mappings
// The column positions in the mappings are off by 1
// This causes debuggers to highlight the wrong character positions
```

When I set breakpoints or inspect errors in the browser devtools, the debugger points to incorrect positions in my original template code. For example, if there's an error in an expression like `{{ message }}`, the debugger might highlight the wrong part of the expression or even a completely different line.

### Expected behavior

Source maps should accurately map generated code positions back to the original template source positions. Debuggers should highlight the exact location in the original template where an error occurred or where a breakpoint was set.

### System Info
- Vue version: 3.x
- Node version: 18.x
- Building with source maps enabled

---
Repository: /testbed
