# Bug Report

### Describe the bug

When using argument descriptions with commands, arguments that have descriptions set are not being displayed in the help output. It seems like the help system is only showing arguments when ALL arguments have descriptions, rather than showing any argument that has a description.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .argument('<source>', 'source file to process')
  .argument('<destination>')  // No description provided
  .action((source, destination) => {
    console.log(`Processing ${source} to ${destination}`);
  });

program.parse();
```

Run with `--help` flag:
```
node myprogram.js --help
```

### Expected behavior

The help output should display the `<source>` argument with its description even though `<destination>` doesn't have a description. Arguments with descriptions should be visible regardless of whether other arguments lack descriptions.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
