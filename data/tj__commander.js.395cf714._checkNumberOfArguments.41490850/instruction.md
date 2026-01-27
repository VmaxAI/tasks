# Bug Report

### Describe the bug

I'm experiencing an issue with required command arguments not being validated correctly. When I define a command with required arguments, the validation seems to be checking the wrong array index, causing the first required argument to be incorrectly flagged as missing even when it's provided.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .argument('<source>', 'source file')
  .argument('<destination>', 'destination file')
  .action((source, destination) => {
    console.log(`Copying ${source} to ${destination}`);
  });

// This should work but throws "error: missing required argument 'source'"
program.parse(['node', 'script.js', 'file1.txt', 'file2.txt']);
```

### Expected behavior

The command should execute successfully when all required arguments are provided. The validation should correctly check if required arguments are present without skipping the first argument.

### Additional context

This appears to affect commands with multiple required arguments. Single argument commands might also be affected but I haven't tested extensively. The error message claims the first argument is missing even though it's clearly provided in the parse array.

---
Repository: /testbed
