# Bug Report

### Describe the bug

I'm experiencing an issue where invalid HTML tag objects are not being properly validated. When passing non-object values (like `null` or primitives), the validation function doesn't throw an error as expected, allowing invalid values to pass through.

### Reproduction

```js
// This should throw an error but doesn't
const invalidTag = null;
// validation passes when it shouldn't

// Also happens with other falsy values
const anotherInvalid = false;
// no error thrown
```

The validation seems to accept values that aren't actually valid HTML tag objects, which causes issues downstream when trying to render them.

### Expected behavior

The validation should reject any value that isn't a proper object with a valid `tagName` property. Non-object values like `null`, `undefined`, numbers, strings, or booleans should all throw validation errors immediately.

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
