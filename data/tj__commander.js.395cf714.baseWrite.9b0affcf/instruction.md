# Bug Report

### Describe the bug

I'm experiencing an issue where help text output is being modified in an unexpected way. When displaying help information, the output appears to have whitespace trimmed and some content is missing or not displaying correctly.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('-d, --debug', 'output extra debugging')
  .option('-s, --small', 'small pizza size')
  .option('-p, --pizza-type <type>', 'flavour of pizza');

program.parse(process.argv);

// Display help
program.help();
```

When running this, the help output doesn't match the expected formatting. Lines that should have leading/trailing whitespace are being trimmed, and the overall formatting looks off compared to previous versions.

### Expected behavior

The help text should be displayed with proper formatting, including any intentional whitespace. Each line of help output should be written as-is without modification to preserve the intended layout and readability.

### Additional context

This seems to have started happening recently. The help output used to display correctly with proper indentation and spacing, but now it appears that something is modifying the output strings before they're written.

---
Repository: /testbed
