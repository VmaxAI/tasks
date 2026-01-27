# Bug Report

### Describe the bug

When a required argument is missing from a command, the error message being displayed is incorrect. Instead of showing the full error message like `error: missing required argument 'filename'`, it only displays the argument name itself (e.g., just `filename`).

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .argument('<filename>', 'file to process')
  .action((filename) => {
    console.log('Processing:', filename);
  });

// Run without providing the required argument
program.parse(['node', 'script.js']);
```

### Expected behavior

Should display: `error: missing required argument 'filename'`

### Actual behavior

Only displays: `filename`

This makes it confusing for users as they don't get the proper context that an argument is missing - they just see the argument name printed out.

### System Info
- commander version: latest
- Node version: 18.x

---
Repository: /testbed
