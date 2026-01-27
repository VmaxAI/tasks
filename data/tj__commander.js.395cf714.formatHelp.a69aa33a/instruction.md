# Bug Report

### Describe the bug

The help output is completely broken and showing garbled/incomplete text. When running any command with `--help` or when help is triggered, instead of showing the properly formatted help message, it appears to be truncated or corrupted.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();
program
  .name('my-cli')
  .description('A sample CLI tool')
  .option('-d, --debug', 'output extra debugging')
  .option('-v, --verbose', 'verbose output');

program.parse();
```

When running:
```bash
node my-cli.js --help
```

### Expected behavior

Should display the full formatted help output with:
- Usage section
- Description
- Options list with proper alignment
- Commands list (if any)

Instead, the output appears to be cut off or showing incomplete/malformed text.

### System Info
- Node version: 18.x
- commander version: latest

This seems to have started happening recently. The help formatting was working fine before.

---
Repository: /testbed
