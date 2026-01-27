# Bug Report

### Describe the bug

When a custom argument parser throws an `InvalidArgumentError`, the error message displayed to the user is incomplete. The actual error details from `err.message` are not being shown, only the error code is displayed.

### Reproduction

```js
const { Command, InvalidArgumentError } = require('commander');

const program = new Command();

program
  .argument('<value>', 'a value', (value) => {
    throw new InvalidArgumentError('Must be a positive number');
  })
  .action(() => {});

program.parse(['node', 'test', 'invalid']);
```

### Expected behavior

The error output should include the full error message: `"error: invalid argument 'invalid' Must be a positive number"`

### Actual behavior

The error output only shows: `"error: invalid argument 'invalid' commander.invalidArgument"` 

The custom error message "Must be a positive number" is missing from the output, making it difficult for users to understand what went wrong with their input.

### System Info
- commander version: latest
- Node version: 18.x

---
Repository: /testbed
