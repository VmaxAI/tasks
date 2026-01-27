# Bug Report

### Describe the bug

I'm experiencing an issue with column position reporting in the template compiler. When parsing templates with content on the first line after a newline, the column numbers in error messages and source locations are off by one.

### Reproduction

```js
const template = `
<div>test</div>`

// When parsing this template, position information for content
// on the line after the newline has incorrect column values
// Expected column for '<div>' to be 1, but getting 0 instead
```

This affects error reporting and source map accuracy when the template has content immediately following a newline character.

### Expected behavior

Column positions should be 1-indexed and correctly calculated for all lines in the template, including lines that come after newline characters. The first character on any line should report column 1, not column 0.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

---
Repository: /testbed
