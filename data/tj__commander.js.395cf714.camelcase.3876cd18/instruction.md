# Bug Report

### Describe the bug

I'm encountering an issue with option name conversion when using hyphenated option names. It seems like the camelCase conversion is not working properly and is producing malformed option names.

### Reproduction

```js
// When using hyphenated option names like:
const option = 'my-option-name';

// The camelCase conversion produces incorrect results
// Expected: 'myOptionName'
// Actual: 'mymy-optionoption-namename' (or similar malformed output)
```

When I try to use options with hyphens in their names, they don't get converted to camelCase correctly. Instead of getting clean camelCase names, the output appears to be duplicating parts of the original string or including unexpected characters.

### Expected behavior

Hyphenated option names should be converted to proper camelCase format. For example:
- `my-option` should become `myOption`
- `some-long-name` should become `someLongName`
- `test-case` should become `testCase`

### System Info
- Node version: 18.x
- Package version: latest

---
Repository: /testbed
