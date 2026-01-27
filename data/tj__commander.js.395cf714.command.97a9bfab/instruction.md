# Bug Report

### Describe the bug

When defining executable subcommands using the `.command()` method with a description parameter, the command is not being recognized as executable and the description is not being set properly.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

// Define an executable subcommand with description
program
  .command('deploy <environment>', 'Deploy to specified environment')
  .option('-f, --force', 'Force deployment');

program.parse(process.argv);
```

When running this code, the subcommand should be marked as executable and have the description "Deploy to specified environment", but instead the behavior is inverted - it only works when no description is provided.

### Expected behavior

The command should:
1. Be marked as an executable command (`_executableHandler` should be true)
2. Have the description set to "Deploy to specified environment"
3. Return the parent command (not the subcommand itself)

### System Info
- commander.js version: latest
- Node.js version: 16.x

This seems to have broken recently as it was working fine before. The logic for handling the description parameter appears to be backwards now.

---
Repository: /testbed
