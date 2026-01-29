# Bug Report

### Describe the bug

When validation warnings are printed, nothing appears in the console even though there are validation errors present. The warning messages seem to be silently ignored.

### Reproduction

```js
// When Joi validation returns a warning with details
const validationResult = someSchema.validate(data, { warnings: true });

// Calling printWarning with the error
printWarning(validationResult.error);

// Expected: Warning messages to be logged
// Actual: Nothing is logged to console
```

### Expected behavior

Validation warning messages should be displayed in the console when `printWarning()` is called with a validation error that contains details.

### Additional context

This seems to have broken recently. Previously, validation warnings were being displayed correctly, but now they're completely silent even when validation issues are present. The function is being called but no output appears.

---
Repository: /testbed
