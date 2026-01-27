# Bug Report

### Describe the bug

I'm experiencing an issue with the `_n` helper function in Vue 3's compatibility mode. When converting string values to numbers, the function is returning incorrect results. Specifically, it seems to be calling `parseFloat()` but then immediately overriding the result with `Number()`, which causes unexpected behavior with certain string inputs.

### Reproduction

```js
// In a Vue 2 compatibility mode component
// Using the _n helper (looseToNumber)

const result1 = _n('123.45')  // Expected: 123.45, but getting incorrect value
const result2 = _n('  42  ')  // Expected: 42, but getting incorrect value
const result3 = _n('3.14abc')  // Expected: 3.14, but getting NaN instead
```

The issue appears when migrating Vue 2 templates that rely on the `_n` helper for number conversion. The converted values don't match what Vue 2 used to produce.

### Expected behavior

The `_n` helper should convert strings to numbers using loose conversion rules (similar to `parseFloat`), allowing partial numeric strings to be converted. For example:
- `'123.45'` should become `123.45`
- `'  42  '` should become `42`
- `'3.14abc'` should become `3.14` (not `NaN`)

This is how it worked in Vue 2 and is necessary for backward compatibility.

### System Info
- Vue version: 3.x (compat mode)
- Migrating from Vue 2

---
Repository: /testbed
