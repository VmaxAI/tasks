# Bug Report

### Describe the bug

Lifecycle hooks are not being executed when using the command framework. I've set up `preAction` and `postAction` hooks on my commands but they're completely silent - no callbacks are being triggered at all.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .hook('preAction', (thisCommand, actionCommand) => {
    console.log('preAction hook called');
  })
  .hook('postAction', (thisCommand, actionCommand) => {
    console.log('postAction hook called');
  });

program
  .command('test')
  .action(() => {
    console.log('Action executed');
  });

program.parse(['node', 'test.js', 'test']);
```

When running this code, I only see "Action executed" printed. The preAction and postAction hooks are never called.

### Expected behavior

Both the preAction and postAction hooks should be invoked before and after the action callback executes. The output should be:
```
preAction hook called
Action executed
postAction hook called
```

This was working fine in previous versions. I suspect something changed recently that broke the hook execution mechanism.

---
Repository: /testbed
