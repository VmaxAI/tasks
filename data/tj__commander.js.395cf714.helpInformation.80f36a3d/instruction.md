# Bug Report

### Describe the bug

Help text color handling seems broken. When I generate help output in contexts where colors should be disabled (like when piping to a file or in CI environments), the output still contains ANSI color codes. Conversely, when colors should be shown in a terminal, they're being stripped out.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();
program
  .name('myapp')
  .description('Test application')
  .option('-d, --debug', 'enable debug mode');

// In a non-TTY context (e.g., piped output), this still returns colored text
const helpText = program.helpInformation();
console.log(helpText);

// Expected: plain text without ANSI codes
// Actual: text with ANSI color codes included
```

You can also test by redirecting output:
```bash
node myapp.js --help > output.txt
# output.txt contains ANSI escape sequences when it shouldn't
```

### Expected behavior

- When outputting to a file or non-TTY context, help text should be plain without color codes
- When outputting to a terminal that supports colors, help text should include color formatting
- The behavior should match what `context.hasColors` indicates

### System Info
- Node version: 18.x
- Commander.js version: latest

---
Repository: /testbed
