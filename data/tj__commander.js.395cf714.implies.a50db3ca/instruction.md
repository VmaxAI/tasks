# Bug Report

### Describe the bug

When using the `implies()` method with a string argument, the implied option is being set to the string value itself instead of `true`. This causes unexpected behavior when checking implied options.

### Reproduction

```js
const { Option } = require('commander');

const option = new Option('-d, --debug', 'enable debug mode');
option.implies('verbose');

// After this, the implied value for 'verbose' is 'verbose' (string)
// instead of true (boolean)
console.log(option.implied); // Expected: { verbose: true }, Actual: { verbose: 'verbose' }
```

### Expected behavior

When passing a string to `implies()`, it should set the implied option value to `true`, not to the string itself. The method should treat a string argument as a shorthand for `{ optionName: true }`.

### Additional context

This worked correctly in previous versions where string arguments were properly converted to boolean `true` values. The current behavior breaks the intended use case where implied options should be enabled (set to `true`) when the parent option is specified.

---
Repository: /testbed
