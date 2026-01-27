# Bug Report

### Describe the bug

Conflicting option detection is not working properly. When I specify two options that are marked as conflicting with each other, no error is raised and both options are processed together. This allows invalid command combinations to execute without any warning.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-a, --option-a', 'First option')
  .option('-b, --option-b', 'Second option')
  .conflictsWith('option-a', 'option-b');

program.parse(['-a', '-b'], { from: 'user' });
// Expected: Error about conflicting options
// Actual: Both options are accepted without error
```

### Expected behavior

When conflicting options are specified together, the program should throw an error indicating that the options cannot be used simultaneously.

### System Info
- Node version: 18.x
- commander version: latest

---
Repository: /testbed
