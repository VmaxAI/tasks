# Bug Report

### Describe the bug

I'm experiencing an issue with subcommand execution where the wrong command is being invoked. When I try to run a subcommand with arguments, it seems like the command lookup is using the wrong parameter.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .command('deploy <env>')
  .action((env) => {
    console.log(`Deploying to ${env}`);
  });

program
  .command('build')
  .action(() => {
    console.log('Building...');
  });

program.parse(['node', 'script.js', 'deploy', 'production']);
```

When running this, the command lookup fails or behaves unexpectedly. It seems like the subcommand dispatcher is not correctly identifying which command to execute.

### Expected behavior

The `deploy` command should be executed with `production` as the `<env>` argument, printing "Deploying to production".

### Additional context

This appears to be related to how subcommands are dispatched and how their operands are passed through. The command name parameter doesn't seem to be used correctly when finding the subcommand to execute.

---
Repository: /testbed
