# Bug Report

### Describe the bug

When using custom argument parsing with `parseArg` and throwing an `InvalidArgumentError`, the error handling seems to cause issues. After the error message is displayed, the program doesn't exit properly in certain cases.

### Reproduction

```js
const { Command, InvalidArgumentError } = require('commander');

const program = new Command();

program
  .argument('<number>', 'a number', (value) => {
    const parsed = parseInt(value);
    if (isNaN(parsed)) {
      throw new InvalidArgumentError('Not a number.');
    }
    return parsed;
  })
  .action((num) => {
    console.log(`Got number: ${num}`);
  });

program.parse(['node', 'test', 'abc']);
```

### Expected behavior

The program should display the error message and exit cleanly. However, it seems like after displaying the custom error message, there's unexpected behavior where the error might propagate further than intended.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
