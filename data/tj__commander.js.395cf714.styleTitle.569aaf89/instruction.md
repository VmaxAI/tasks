# Bug Report

### Describe the bug

After a recent update, the help text titles are being transformed in an unexpected way. It looks like some automatic capitalization logic is being applied to titles, which is changing the formatting of properly cased strings.

### Reproduction

```js
const help = new Help();

// Example 1: Acronyms are being lowercased incorrectly
const title1 = help.styleTitle('API Reference');
console.log(title1); // Expected: "API Reference", Got: "Api Reference"

// Example 2: camelCase identifiers are being mangled
const title2 = help.styleTitle('myFunction Options');
console.log(title2); // Expected: "myFunction Options", Got: "Myfunction Options"

// Example 3: ALL CAPS titles are being converted
const title3 = help.styleTitle('HTTP METHODS');
console.log(title3); // Expected: "HTTP METHODS", Got: "Http Methods"
```

### Expected behavior

The `styleTitle()` method should preserve the original casing of the input string. If a user passes in "API Reference", it should stay as "API Reference", not be converted to "Api Reference". Same goes for camelCase identifiers and other intentional formatting.

This is breaking our documentation where we have specific casing requirements for technical terms, acronyms, and code identifiers.

### System Info
- Node version: 18.x
- Package version: latest

---
Repository: /testbed
