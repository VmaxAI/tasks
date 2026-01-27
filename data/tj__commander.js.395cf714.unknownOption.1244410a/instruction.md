# Bug Report

### Describe the bug

When using an unknown option flag, the error message doesn't show helpful suggestions for similar valid options. The suggestion feature seems to be broken and no alternatives are displayed even when there are clearly similar option names available.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('--verbose', 'enable verbose mode')
  .option('--output <file>', 'output file')
  .option('--format <type>', 'format type');

// Try using a typo in an option name
program.parse(['node', 'test', '--verbos']);
```

### Expected behavior

Should display an error message with a suggestion like:
```
error: unknown option '--verbos'
(Did you mean --verbose?)
```

But instead it just shows:
```
error: unknown option '--verbos'
```

The suggestion part is completely missing even though `--verbose` is a very close match.

### System Info
- Node version: 18.x
- Commander.js version: latest

---
Repository: /testbed
