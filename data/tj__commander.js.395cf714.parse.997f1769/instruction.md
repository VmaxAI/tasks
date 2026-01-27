# Bug Report

### Describe the bug

I'm experiencing an issue with command parsing where arguments are being processed in the wrong order. When I pass arguments to my CLI application, they're not being recognized correctly and the command fails to execute as expected.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .argument('<source>', 'source file')
  .argument('<destination>', 'destination file')
  .action((source, destination) => {
    console.log('source:', source);
    console.log('destination:', destination);
  });

program.parse(['node', 'script.js', 'file1.txt', 'file2.txt']);
```

When running this code, the arguments seem to be swapped or not parsed properly. The command doesn't receive the arguments in the correct positions.

### Expected behavior

The command should parse the arguments in order and pass them to the action handler correctly. `source` should be 'file1.txt' and `destination` should be 'file2.txt'.

### Additional context

This seems to have started happening recently. The argument parsing was working fine before. Not sure if this is related to any recent changes in how arguments are processed internally.

---
Repository: /testbed
