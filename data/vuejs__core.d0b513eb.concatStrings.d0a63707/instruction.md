# Bug Report

### Describe the bug

I'm experiencing an issue with string concatenation in compiled SFC output. When multiple strings are joined together, the spacing around commas is incorrect - there's a space before the comma instead of after it. This produces malformed output that doesn't match the expected format.

### Reproduction

When the compiler concatenates multiple string values (for example, in component props or other declarations), the output has incorrect comma spacing:

```js
// Expected output: "foo, bar, baz"
// Actual output: "foo ,bar ,baz"
```

This affects any scenario where multiple string values need to be combined into a single comma-separated string.

### Expected behavior

Strings should be joined with proper comma-space formatting (`, `) rather than space-comma (` ,`). The output should be `"foo, bar, baz"` not `"foo ,bar ,baz"`.

### System Info
- Vue version: 3.x
- Package: @vue/compiler-sfc

---
Repository: /testbed
