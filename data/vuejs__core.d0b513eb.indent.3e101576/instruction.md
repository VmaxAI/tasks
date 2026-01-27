# Bug Report

### Describe the bug

I'm experiencing an issue with code generation where the indentation in the generated code is off by one level. When the compiler generates code with nested structures, the first indentation level appears to be missing, causing the entire block to be indented incorrectly.

### Reproduction

```js
// When compiling a template with nested elements
const template = `
  <div>
    <span>
      <p>nested content</p>
    </span>
  </div>
`

// The generated code has incorrect indentation
// Expected: proper indentation starting from the first level
// Actual: first indent is skipped, subsequent indents are off
```

### Expected behavior

The generated code should have proper indentation at all levels, with each nested block correctly indented relative to its parent. The first call to indent should increase the indentation level before writing the newline.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

This seems to affect any template compilation that uses indentation, particularly noticeable with deeply nested structures.

---
Repository: /testbed
