# Bug Report

### Describe the bug

I'm experiencing an issue with command parsing where the arguments are being processed in the wrong order. When using `parseAsync()`, it seems like the operands and arguments are getting swapped, causing commands to fail or behave unexpectedly.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .argument('<file>', 'file to process')
  .option('-o, --output <path>', 'output path')
  .action((file, options) => {
    console.log('File:', file);
    console.log('Options:', options);
  });

await program.parseAsync(['node', 'script.js', 'input.txt', '-o', 'output.txt']);
```

### Expected behavior

The command should correctly parse `input.txt` as the file argument and `-o output.txt` as the option. However, the parsing seems to be mixing up the order internally, leading to incorrect argument assignment.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
