# Bug Report

### Describe the bug

I'm encountering an issue with `passThroughOptions` validation in subcommands. When I try to use `passThroughOptions` on a subcommand whose parent has `enablePositionalOptions` enabled, I'm getting an error that shouldn't be thrown.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();
program.enablePositionalOptions();

const subcommand = program
  .command('sub')
  .passThroughOptions();

// This throws an error even though the parent has enablePositionalOptions enabled
program.parse(['node', 'test', 'sub', '--', 'extra', 'args']);
```

### Expected behavior

The subcommand should work correctly when `passThroughOptions` is used and the parent command has `enablePositionalOptions` enabled. The validation check should pass in this case and allow the command to execute normally.

### Additional context

This seems to be a validation issue where the check for `passThroughOptions` compatibility is incorrectly rejecting valid configurations. The error message suggests that `enablePositionalOptions` needs to be turned on for parent commands, but it already is enabled.

---
Repository: /testbed
