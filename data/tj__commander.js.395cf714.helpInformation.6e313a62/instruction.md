# Bug Report

### Describe the bug

The help text output is showing ANSI color codes in terminals that don't support colors. When running the help command in a non-color terminal or piping output to a file, the escape sequences are visible in the output instead of being stripped.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();
program
  .name('myapp')
  .description('Test application')
  .option('-d, --debug', 'enable debug mode');

// Run in a terminal without color support or redirect output
// The help text will contain ANSI escape codes instead of plain text
console.log(program.helpInformation());
```

Or from command line:
```bash
node myapp.js --help > output.txt
# output.txt contains escape sequences like \x1b[33m instead of plain text
```

### Expected behavior

When the terminal doesn't support colors (or when `hasColors` is false), the help text should be plain text without any ANSI escape sequences. Color codes should only appear when the terminal supports them.

### System Info
- commander version: latest
- Node version: 18.x
- OS: Linux/macOS

---
Repository: /testbed
