# Bug Report

### Describe the bug

I'm experiencing an issue with color output in help text. When colors are supported by the terminal, the help output is showing ANSI escape codes stripped out, making the text appear without any formatting. Conversely, when colors are NOT supported, the ANSI codes are being displayed as raw text instead of being stripped.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .name('myapp')
  .description('A test application')
  .option('-d, --debug', 'enable debug mode');

// In a terminal that supports colors
program.outputHelp();
// Expected: colored output
// Actual: plain text without colors

// In a terminal that doesn't support colors  
program.outputHelp();
// Expected: plain text
// Actual: raw ANSI escape codes visible
```

### Expected behavior

When the terminal supports colors, help text should display with colors/formatting. When colors are not supported, the ANSI codes should be stripped and plain text should be shown.

### System Info
- commander version: latest
- Node.js version: 18.x
- OS: Linux

The behavior seems inverted - it's stripping colors when they should be shown and showing escape codes when they should be stripped.

---
Repository: /testbed
