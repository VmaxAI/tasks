# Bug Report

### Describe the bug

When using `.choices()` to restrict option values, the validation logic appears to be inverted. Valid choices are being rejected with an error message, while invalid choices are being accepted without any error.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-c, --color <type>', 'choose color')
  .choices(['red', 'green', 'blue']);

program.parse(['node', 'test', '--color', 'red']);
```

When running this code with a valid choice like 'red', it throws an error:
```
error: Allowed choices are red, green, blue.
```

But if you pass an invalid choice like 'yellow', it gets accepted without any validation error.

### Expected behavior

- Valid choices from the defined list should be accepted
- Invalid choices should throw an `InvalidArgumentError` with the message about allowed choices
- The validation should work correctly for both variadic and non-variadic options

### System Info
- commander version: latest
- Node.js version: 18.x

This seems like a regression as choice validation was working correctly before. The error message itself is correct but it's being triggered for the wrong values.

---
Repository: /testbed
