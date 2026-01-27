# Bug Report

### Describe the bug

When defining a subcommand with a description string, the parent command is not being returned correctly. This breaks method chaining when trying to add multiple executable subcommands to a parent command.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .command('serve <dir>', 'start a web server')
  .command('build <dir>', 'build the project')
  .parse(process.argv);
```

### Expected behavior

The parent `program` command should be returned after each `.command()` call when using the executable subcommand syntax (with description string), allowing for proper method chaining. Currently it appears to be returning the subcommand instead, which breaks the chain.

This used to work in previous versions but seems to have regressed recently.

### System Info
- Node version: v18.x
- commander version: latest

---
Repository: /testbed
