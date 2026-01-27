# Bug Report

### Describe the bug

Lifecycle hooks are not being executed when commands are run. I've registered `preAction` and `postAction` hooks on my commands, but they're completely silent - none of the callbacks are being triggered.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .hook('preAction', (thisCommand, actionCommand) => {
    console.log('This should print before action');
  })
  .hook('postAction', (thisCommand, actionCommand) => {
    console.log('This should print after action');
  });

program
  .command('test')
  .action(() => {
    console.log('Action executed');
  });

program.parse(['node', 'test.js', 'test']);
```

### Expected behavior

The hooks should fire before and after the action:
```
This should print before action
Action executed
This should print after action
```

### Actual behavior

Only the action executes:
```
Action executed
```

The hook callbacks are registered but never called. This breaks my entire command workflow that relies on these hooks for logging and cleanup.

### System Info
- commander version: latest
- Node.js: v18.x

---
Repository: /testbed
