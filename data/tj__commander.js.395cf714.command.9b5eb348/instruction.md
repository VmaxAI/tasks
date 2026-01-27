# Bug Report

### Describe the bug

When defining subcommands with options objects, the command registration is not working as expected. The parent command is being returned instead of the subcommand, which breaks the ability to chain method calls on the newly created subcommand.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

// This should return the subcommand for further configuration
const subCmd = program.command('serve', { isDefault: true });

// Trying to add options or actions to subCmd fails because
// it's actually the parent program, not the subcommand
subCmd.option('-p, --port <number>', 'port number');
```

### Expected behavior

When calling `.command()` with an options object (like `{ isDefault: true }`), it should return the newly created subcommand so that it can be further configured with options, arguments, and actions. The parent command should only be returned when creating an executable subcommand with a description string.

### System Info
- commander version: latest
- Node version: 18.x

This seems to have broken recently - the command API used to work correctly when passing options objects to register default commands or configure subcommand behavior.

---
Repository: /testbed
