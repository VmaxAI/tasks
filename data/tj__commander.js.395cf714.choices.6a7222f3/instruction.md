# Bug Report

### Describe the bug

When using the `choices()` method on an Argument, the first choice in the array is being excluded and validation fails even when providing valid choices from the original list.

### Reproduction

```js
const { Argument } = require('commander');

const arg = new Argument('<color>', 'Choose a color')
  .choices(['red', 'green', 'blue']);

// This should work but throws an error
// Error: Allowed choices are green, blue.
// 'red' is missing from the allowed choices!
```

### Expected behavior

All values passed to `choices()` should be valid options. In the example above, 'red', 'green', and 'blue' should all be accepted as valid arguments.

### System Info
- Node version: 18.x
- commander version: latest

---
Repository: /testbed
