# Bug Report

### Describe the bug

When trying to make an argument required using `argRequired()`, the argument is not actually being set as required. The method seems to have no effect and arguments remain optional even after calling `argRequired()`.

### Reproduction

```js
const { Argument } = require('commander');

const arg = new Argument('<file>', 'file to process');
arg.argRequired();

// The argument should now be required, but it's not being set correctly
console.log(arg.required); // Expected: true, Actual: undefined or false
```

### Expected behavior

After calling `argRequired()`, the `required` property should be set to `true` and the argument should be treated as required by the parser.

### Additional context

This appears to have broken recently. The method returns the Argument instance correctly for chaining, but the internal state is not being updated as expected.

---
Repository: /testbed
