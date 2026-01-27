# Bug Report

### Describe the bug

When using `parseAsync()` with commands that have async action handlers, the promise returned by `parseAsync()` resolves immediately before the action handlers complete execution. This means that any code awaiting `parseAsync()` will continue before the command has actually finished processing.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .command('test')
  .action(async () => {
    await new Promise(resolve => setTimeout(resolve, 1000));
    console.log('Action completed');
  });

// This returns before "Action completed" is printed
await program.parseAsync(['node', 'script.js', 'test']);
console.log('parseAsync resolved');

// Expected output order:
// Action completed
// parseAsync resolved

// Actual output order:
// parseAsync resolved
// Action completed
```

### Expected behavior

`parseAsync()` should wait for all async action handlers to complete before resolving the returned promise. The whole point of having an async version of parse is to be able to await the full command execution.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
