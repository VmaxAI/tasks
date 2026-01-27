# Bug Report

### Describe the bug

Arguments are not being displayed in the help output. When running `--help` or accessing help text, the argument names/descriptions appear to be missing from the generated help message.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .argument('<file>', 'file to process')
  .argument('[output]', 'optional output file')
  .action((file, output) => {
    console.log('Processing:', file, output);
  });

program.parse();
```

Run with `--help`:
```
$ node script.js --help
```

### Expected behavior

The help output should display the argument names and descriptions:
```
Usage: script [options] <file> [output]

Arguments:
  file          file to process
  output        optional output file
```

### Actual behavior

The argument text is not showing up in the help output - it appears blank or empty where the argument information should be displayed.

### System Info
- commander version: latest
- Node version: 18.x

---
Repository: /testbed
