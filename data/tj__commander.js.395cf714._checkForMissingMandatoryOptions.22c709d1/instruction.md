# Bug Report

### Describe the bug

I'm experiencing an issue where mandatory options are being flagged as missing even when they are provided. After parsing command-line arguments, the program incorrectly throws an error about missing mandatory options that were actually supplied.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('-r, --required <value>', 'A required option', { mandatory: true })
  .option('-o, --optional <value>', 'An optional option');

// This should work but throws an error about missing mandatory option
program.parse(['-r', 'test-value'], { from: 'user' });
```

When running this code with the required option provided, it still complains that the mandatory option is missing.

### Expected behavior

When a mandatory option is provided via command-line arguments, the program should accept it and continue execution without throwing an error. The validation should only trigger when the mandatory option is actually missing.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
