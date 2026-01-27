# Bug Report

### Describe the bug

When using the `.choices()` method to restrict option values, the validation is inverted - valid choices are being rejected while invalid choices are being accepted. Additionally, for variadic options, the previous value is being returned instead of concatenating the new value.

### Reproduction

```js
const program = new Command();
program
  .option('-c, --color <color>', 'choose color')
  .choices(['red', 'green', 'blue']);

// This should work but throws an error
program.parse(['node', 'test', '--color', 'red']);

// This should throw an error but is accepted
program.parse(['node', 'test', '--color', 'yellow']);
```

For variadic options:
```js
program
  .option('-t, --tags <tags...>', 'select tags')
  .choices(['urgent', 'bug', 'feature']);

// Multiple valid values don't accumulate properly
program.parse(['node', 'test', '--tags', 'urgent', 'bug']);
// Expected: ['urgent', 'bug']
// Actual: previous value is returned instead
```

### Expected behavior

- Valid choices should be accepted without errors
- Invalid choices should throw an `InvalidArgumentError`
- Variadic options should accumulate values correctly

### System Info
- Node version: 18.x
- Package version: latest

---
Repository: /testbed
