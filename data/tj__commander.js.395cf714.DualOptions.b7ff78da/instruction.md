# Bug Report

### Describe the bug

I'm experiencing an issue with dual options (options that support both positive and negative forms like `--foo` and `--no-foo`). The logic for detecting which options should be treated as dual options seems inverted - options are being incorrectly classified.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('--color', 'enable color')
  .option('--no-color', 'disable color');

program.parse(['node', 'test', '--color']);

// The option is not being recognized correctly as a dual option
// Expected: --color and --no-color should both be available
// Actual: Only one form is recognized
```

When I define both a positive option (like `--color`) and its negative counterpart (`--no-color`), only one of them gets properly registered as a dual option. It seems like the detection logic is backwards.

### Expected behavior

Both the positive and negative forms of an option should be recognized and work correctly. When I specify `--color`, it should enable color, and when I specify `--no-color`, it should disable color.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
