# Bug Report

### Describe the bug

When displaying help text for commands with arguments, the arguments section is not showing up even when argument descriptions are provided. It seems like the visibility logic for arguments got inverted somehow.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .argument('<source>', 'source file to process')
  .argument('[destination]', 'destination file (optional)')
  .action((source, destination) => {
    console.log('source:', source);
    console.log('destination:', destination);
  });

program.parse();
```

When running with `--help`, the arguments section doesn't appear in the help output even though descriptions are defined for both arguments.

### Expected behavior

The help output should display the arguments section with their descriptions when argument descriptions are provided. Arguments without descriptions should be hidden from the help text.

### System Info
- commander.js version: latest
- Node version: 18.x

---
Repository: /testbed
