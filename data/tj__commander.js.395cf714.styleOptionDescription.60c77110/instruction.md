# Bug Report

### Describe the bug

When using `styleOptionDescription()` method, passing an empty string or falsy value returns the original value instead of applying the description text styling. This is inconsistent with other similar methods like `styleCommandDescription()` and `styleSubcommandDescription()` which properly apply styling to all inputs.

### Reproduction

```js
const help = new Help();

// This returns empty string instead of styled text
const result = help.styleOptionDescription('');
console.log(result); // Expected: styled empty string, Actual: ''

// For comparison, this works as expected
const cmdResult = help.styleCommandDescription('');
console.log(cmdResult); // Returns properly styled text
```

### Expected behavior

The `styleOptionDescription()` method should apply styling consistently with other description styling methods, regardless of whether the input is an empty string or other falsy value. It should call `styleDescriptionText()` in all cases.

### System Info
- Node version: 18.x
- Package version: latest

---
Repository: /testbed
