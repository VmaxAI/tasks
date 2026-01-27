# Bug Report

### Describe the bug

I'm experiencing an issue with option names that start with a hyphen. When using options like `--option` or similar patterns, the camelCase conversion doesn't work as expected and causes unexpected behavior.

### Reproduction

```js
// When an option name starts with a hyphen or has multiple consecutive hyphens
const option1 = camelcase('-option')
const option2 = camelcase('--double-option')

// These produce incorrect results
console.log(option1) // Expected: 'option', but getting something else
console.log(option2) // Expected: 'doubleOption', but getting something else
```

### Expected behavior

Option names with leading hyphens should be properly converted to camelCase format. For example:
- `-option` should become `option`
- `--double-option` should become `doubleOption`
- `my-option` should become `myOption`

The camelCase conversion should handle edge cases with hyphens at the beginning or multiple consecutive hyphens.

---
Repository: /testbed
