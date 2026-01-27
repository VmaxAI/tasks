# Bug Report

### Describe the bug

The code generator is producing malformed output when generating node lists with multiple nodes. The generated code contains duplicate commas in certain cases, resulting in invalid JavaScript syntax.

### Reproduction

```js
// When compiling a template with multiple child nodes
const template = `
  <div>
    <span>First</span>
    <span>Second</span>
    <span>Third</span>
  </div>
`

// The generated code contains syntax errors with duplicate commas
// Expected: createVNode("span"), createVNode("span"), createVNode("span")
// Actual: createVNode("span"),, createVNode("span"),, createVNode("span")
```

This appears to affect templates with multiple sibling elements when the compiler generates the render function code.

### Expected behavior

The code generator should produce valid JavaScript with proper comma separation between nodes. Each node should be separated by a single comma, not multiple commas.

### System Info
- Vue version: 3.x
- Node version: 18.x

---
Repository: /testbed
