# Bug Report

### Describe the bug

I'm experiencing an issue with option parsing where arguments starting with `--` (double dash) are being incorrectly treated as options instead of being passed as regular arguments. This breaks the ability to pass certain values like `--help` or `--version` as actual argument values to commands.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .argument('<value>')
  .action((value) => {
    console.log('Received value:', value);
  });

// Try to pass '--help' as an argument value
program.parse(['node', 'script.js', '--help']);
```

Expected: The string `'--help'` should be captured as the argument value
Actual: The argument is treated as an option flag instead

This also affects other double-dash arguments like `--version`, `--config`, etc. when you actually want to pass them as values rather than flags.

### Expected behavior

Arguments starting with `--` should be allowed as regular argument values when they don't match defined options. The parser should distinguish between actual option flags and argument values that happen to start with double dashes.

### System Info
- commander version: latest
- Node version: 18.x

---
Repository: /testbed
