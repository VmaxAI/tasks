# Bug Report

### Describe the bug

The `string-literal-i18n-messages` ESLint rule is not detecting violations in `translate()` function calls. The rule should report errors when the translate function is called with invalid arguments, but it's currently not catching these cases.

### Reproduction

```js
// This should be flagged but isn't
translate({
  message: someVariable
});

// This should also be flagged but isn't
translate('just a string');
```

The rule seems to be ignoring `translate()` calls entirely instead of validating them.

### Expected behavior

The ESLint rule should report violations when:
1. `translate()` is called without an object expression as the first argument
2. The `message` property contains a template literal with expressions or a non-string value

### Additional context

This appears to have started happening recently. The rule worked correctly before and would catch improper usage of the translate function. Now it seems to skip validation completely for translate calls.

---
Repository: /testbed
