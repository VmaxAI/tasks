# Bug Report

### Describe the bug

I'm encountering an issue with option flag parsing when defining options with both short and long flags. When I specify the short flag before the long flag (e.g., `-s, --long`), the flags get assigned incorrectly. The short flag ends up being treated as the long flag and vice versa.

### Reproduction

```js
const program = require('commander');

program
  .option('-v, --verbose', 'enable verbose output')
  .parse(process.argv);

// Using the short flag
// Expected: program.opts().verbose should be true
// Actual: The flag is not recognized correctly
```

When I run this with `-v`, the option doesn't get parsed as expected. It seems like the order of flag detection has changed and short flags that come before long flags are being mishandled.

### Expected behavior

Both of these should work correctly:
- `-v` should set the verbose option to true
- `--verbose` should set the verbose option to true

The parser should correctly identify which flag is short and which is long regardless of their order in the option string.

### System Info
- Node version: 18.x
- commander version: latest

---
Repository: /testbed
