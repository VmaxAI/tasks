# Bug Report

### Describe the bug

I'm experiencing an issue with the help text formatting where extra spaces are being added to description text. When displaying help information, all descriptions now have trailing spaces appended to them, and multiple consecutive spaces in the original text are being collapsed into single spaces.

### Reproduction

```js
const help = new Help();

// Original description with multiple spaces
const desc = "This is  a  description";
const styled = help.styleDescriptionText(desc);

console.log(styled);
// Expected: "This is  a  description"
// Actual: "This is a description "
```

Also, empty or whitespace-only strings are being replaced with a single space:

```js
const emptyDesc = "";
const styledEmpty = help.styleDescriptionText(emptyDesc);

console.log(styledEmpty);
// Expected: ""
// Actual: " "
```

### Expected behavior

The `styleDescriptionText` method should return the input string unchanged, preserving the original spacing and not adding any trailing spaces. Empty strings should remain empty.

### System Info
- Node version: 18.x
- OS: macOS

---
Repository: /testbed
