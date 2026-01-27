# Bug Report

### Describe the bug

Lifecycle hooks are not being called for subcommands. When I register a hook (like `preSubcommand` or `postSubcommand`) on a parent command, the hook doesn't execute when a subcommand is invoked.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program.hook('preSubcommand', (thisCommand, subCommand) => {
  console.log('Hook called!');
  console.log('Parent:', thisCommand.name());
  console.log('Subcommand:', subCommand.name());
});

program
  .command('sub')
  .action(() => {
    console.log('Subcommand executed');
  });

program.parse(['node', 'test', 'sub']);
```

### Expected behavior

When running the subcommand, the hook should be called and I should see:
```
Hook called!
Parent: [parent command name]
Subcommand: sub
Subcommand executed
```

### Actual behavior

The hook is never invoked, only the subcommand action runs:
```
Subcommand executed
```

This seems to have broken recently - hooks were working fine before. The hooks are registered correctly but just don't fire when subcommands are executed.

---
Repository: /testbed
