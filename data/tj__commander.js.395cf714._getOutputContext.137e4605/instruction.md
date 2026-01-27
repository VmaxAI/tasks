# Bug Report

### Describe the bug

I'm experiencing an issue with color output in help text and error messages. When colors are enabled for standard output, they appear in error messages instead, and vice versa. Additionally, colored output is being stripped when colors are actually enabled, and plain text is shown when colors should be disabled.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// Configure output with colors enabled for stdout
program.configureOutput({
  writeOut: (str) => process.stdout.write(str),
  writeErr: (str) => process.stderr.write(str),
  getOutHasColors: () => true,
  getErrHasColors: () => false,
  stripColor: (str) => str.replace(/\x1b\[\d+m/g, '')
});

program
  .option('-d, --debug', 'enable debug mode')
  .action(() => {
    console.log('Action executed');
  });

// Try to display help - colors should appear in stdout
program.outputHelp();

// Try to display error - should be plain text in stderr
program.error('Test error message');
```

### Expected behavior

- When `getOutHasColors()` returns `true`, help text written to stdout should include color codes
- When `getErrHasColors()` returns `false`, error messages written to stderr should have colors stripped
- The color settings for stdout and stderr should not be swapped

### Current behavior

The color settings appear to be reversed - stdout uses the stderr color configuration and stderr uses the stdout color configuration. Also, colors are being stripped when they should be shown, and shown when they should be stripped.

---
Repository: /testbed
