# Bug Report

### Describe the bug

The help text formatting for command options appears broken. When displaying help output, the option descriptions are not properly aligned anymore. It looks like the column width calculation is incorrect - all options are being aligned to the narrowest option term instead of the widest one.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('-s, --short', 'Short option')
  .option('-v, --very-long-option-name', 'Long option')
  .option('-m, --medium', 'Medium option');

program.parse();
```

When running with `--help`, the alignment is off. The descriptions should align to the longest option term width, but they seem to be aligning to the shortest instead.

### Expected behavior

All option descriptions should be aligned in a column based on the width of the longest option term. For example:

```
Options:
  -s, --short                  Short option
  -v, --very-long-option-name  Long option
  -m, --medium                 Medium option
```

Instead, the formatting appears misaligned.

### System Info
- commander version: latest
- Node.js version: v18.x

---
Repository: /testbed
