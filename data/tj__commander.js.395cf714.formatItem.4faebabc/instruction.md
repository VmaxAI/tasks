# Bug Report

### Describe the bug

The help text formatting appears broken when displaying command options or arguments with descriptions. The alignment is completely off - descriptions are shifted way too far to the right, making the help output unreadable.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-v, --verbose', 'Enable verbose output')
  .option('-f, --file <path>', 'Specify input file')
  .option('-o, --output <path>', 'Specify output file');

program.parse();
```

When running `node script.js --help`, the description text for each option is aligned incorrectly - there's way too much padding between the option names and their descriptions.

### Expected behavior

The help output should have consistent, readable alignment between option names and their descriptions, with appropriate spacing that doesn't push the descriptions too far to the right.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
