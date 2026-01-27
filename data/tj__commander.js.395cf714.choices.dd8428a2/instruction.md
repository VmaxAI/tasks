# Bug Report

### Describe the bug

When using `.choices()` on variadic arguments, the validation against allowed choices is not being enforced. Arguments are accepted even when they don't match any of the specified choices.

### Reproduction

```js
const { Argument } = require('commander');

const arg = new Argument('<items...>')
  .choices(['apple', 'banana', 'orange']);

// This should throw an error but doesn't
try {
  arg.parseArg('grape', []);
  console.log('No error thrown - BUG!');
} catch (e) {
  console.log('Error correctly thrown:', e.message);
}
```

### Expected behavior

Variadic arguments should still validate each value against the allowed choices. Invalid values should throw an `InvalidArgumentError` with the message "Allowed choices are apple, banana, orange."

### Additional context

This seems to affect variadic arguments specifically. Non-variadic arguments with choices work as expected.

---
Repository: /testbed
