# Bug Report

### Describe the bug

I'm experiencing an issue with lifecycle hooks execution order in command hierarchies. When using hooks like `preAction` or `preSubcommand`, they seem to be executing in the wrong order - parent command hooks are running before child command hooks instead of after.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .hook('preAction', (thisCommand, actionCommand) => {
    console.log('Parent preAction hook');
  });

program
  .command('sub')
  .hook('preAction', (thisCommand, actionCommand) => {
    console.log('Child preAction hook');
  })
  .action(() => {
    console.log('Action');
  });

program.parse(['node', 'test', 'sub']);
```

Current output:
```
Parent preAction hook
Child preAction hook
Action
```

### Expected behavior

For `preAction` and similar hooks (non-postAction), child hooks should execute first, then parent hooks. The expected output should be:

```
Child preAction hook
Parent preAction hook
Action
```

This ordering makes sense because "pre" hooks should execute from the innermost command outward, while "post" hooks execute from outermost inward.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
