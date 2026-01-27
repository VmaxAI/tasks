# Bug Report

### Describe the bug

I'm experiencing an issue with optional options not being recognized correctly. When I define an option with square brackets `[]` to indicate it's optional, the library treats it as if it were required (using angle brackets `<>`).

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-f, --file [path]', 'optional file path')
  .parse(process.argv);

// The option should be recognized as optional, but it's being treated as required
```

When I check the option properties:
```js
const option = program.options.find(opt => opt.long === '--file');
console.log(option.optional); // Expected: true, but getting: false
console.log(option.required); // Expected: false, but getting: true
```

### Expected behavior

Options defined with square brackets `[value]` should have `optional = true` and `required = false`. Currently, both properties are being set based on the presence of angle brackets `<>` instead of square brackets.

### Additional context

This seems to affect how the library validates whether a value is needed when the option is specified on the command line. Optional options should allow the flag to be present without requiring a value.

---
Repository: /testbed
