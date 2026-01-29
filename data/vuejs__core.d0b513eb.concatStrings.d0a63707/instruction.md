# Bug Report

### Describe the bug

I'm experiencing an issue with string concatenation in the SFC compiler. When multiple strings are being joined together, the output format is incorrect - there's an extra space before the comma and falsy values (like empty strings) are being included when they shouldn't be.

### Reproduction

```js
// When compiling a component with multiple imports or declarations
// The generated code has incorrect formatting

// For example, with code that should generate:
// "foo, bar, baz"

// It's actually generating:
// "foo ,bar ,baz"  // wrong spacing
// or including empty values that should be filtered out
```

### Expected behavior

The concatenated strings should:
1. Have proper comma-space separation (`, ` not ` ,`)
2. Filter out falsy values like empty strings, null, undefined, and false
3. Produce clean, properly formatted output like `"foo, bar, baz"`

### System Info
- Vue version: 3.x
- Using SFC compiler

---
Repository: /testbed
