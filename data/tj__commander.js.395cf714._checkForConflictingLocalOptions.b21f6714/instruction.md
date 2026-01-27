# Bug Report

### Describe the bug

Conflicting options are not being detected properly. When I specify two options that are marked as conflicting with each other, the command doesn't throw an error as expected. The program just runs normally even though the options shouldn't be used together.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('-a, --option-a', 'First option')
  .option('-b, --option-b', 'Second option')
  .conflictsWith('option-b');

// This should error but doesn't
program.parse(['-a', '-b'], { from: 'user' });
```

### Expected behavior

The command should detect that `--option-a` and `--option-b` are conflicting and throw an error when both are provided. Instead, it allows both options to be used simultaneously without any warning or error.

### Additional context

This seems to affect all cases where conflicting options are defined. The conflict detection mechanism doesn't seem to be working at all in the current version.

---
Repository: /testbed
