# Bug Report

### Describe the bug

The usage string generation is broken when `helpOption(false)` is used to disable the help option. The usage string incorrectly includes `[options]` even when there are no other options defined and the help option has been explicitly disabled.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();
program
  .helpOption(false)  // Disable help option
  .argument('<file>');

console.log(program.usage());
// Outputs: "[options] <file>"
// Expected: "<file>"
```

When the help option is disabled and no other options are defined, the usage string should not include `[options]`.

### Expected behavior

The usage string should only show `[options]` when there are actual options available (either custom options or the help option is enabled).

Expected output: `<file>`
Actual output: `[options] <file>`

### System Info
- commander version: latest
- Node version: 18.x

---
Repository: /testbed
