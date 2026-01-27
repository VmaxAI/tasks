# Bug Report

### Issue with hook parameter order in subcommand lifecycle events

I've noticed that when using lifecycle hooks with subcommands, the parameters passed to the hook function seem to be in the wrong order. The documentation and examples suggest the parent command should come first, but it appears the subcommand is being passed as the first parameter instead.

### Reproduction
```js
const { Command } = require('commander');

const program = new Command();

program.hook('preSubcommand', (thisCommand, subCommand) => {
  console.log('Parent command:', thisCommand.name());
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
The hook should receive the parent command as the first parameter and the subcommand as the second parameter, so that `thisCommand` refers to the parent and `subCommand` refers to the subcommand being executed.

### Actual behavior
The parameters appear to be swapped - the subcommand is passed first and the parent command second.

This is causing issues in our codebase where we rely on the parameter order to access the correct command context. Is this intentional or a bug?

---
Repository: /testbed
