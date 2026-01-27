# Bug Report

### Describe the bug

Lifecycle hooks (like `preAction` and `postAction`) are not being executed at all. I have registered hooks on my commands but they never get called when the command runs.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .command('test')
  .hook('preAction', (thisCommand, actionCommand) => {
    console.log('This should print before action');
  })
  .action(() => {
    console.log('Action executed');
  });

program.parse(['node', 'test.js', 'test']);
```

### Expected behavior

The hook callback should execute and print "This should print before action" before the action runs. Currently, only "Action executed" is printed and the hook is completely ignored.

This affects both `preAction` and `postAction` hooks. I've also tested with parent commands that have hooks - those aren't working either.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
