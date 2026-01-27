# Bug Report

### Describe the bug

Mandatory options are being incorrectly flagged as missing even when they are provided with valid values. The command throws an error about missing mandatory options despite the options being present.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .requiredOption('-u, --user <name>', 'user name')
  .action((options) => {
    console.log('User:', options.user);
  });

// This should work but throws an error about missing mandatory option
program.parse(['-u', 'john'], { from: 'user' });
```

### Expected behavior

When a mandatory option is provided with a value, the command should execute successfully without throwing a "missing mandatory option" error. The action callback should be invoked with the parsed options.

### Actual behavior

The program throws an error indicating that the mandatory option is missing, even though it was provided on the command line.

### Additional context

This appears to affect all required options defined with `.requiredOption()`. The validation logic seems to be incorrectly detecting provided options as missing.

---
Repository: /testbed
