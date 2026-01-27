# Bug Report

### Describe the bug

I'm experiencing an issue where option descriptions in the help output are being processed twice. It looks like the description text styling is being applied redundantly, which could cause performance issues or unexpected behavior with the formatted output.

### Reproduction

```js
const program = require('commander');

program
  .option('-v, --verbose', 'enable verbose mode  ')
  .option('-d, --debug', 'enable debug output   ')
  .parse();

program.help();
```

When the help is displayed, option descriptions appear to be going through the styling process multiple times instead of just once.

### Expected behavior

Option descriptions should only be styled once, similar to how command descriptions and subcommand descriptions are handled. The styling function should be called a single time per description.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
