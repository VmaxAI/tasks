# Bug Report

### Describe the bug

When creating subcommands, the `_allowExcessArguments` setting is not being inherited from the parent command. This causes subcommands to behave differently than expected when excess arguments are passed.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

// Configure parent to allow excess arguments
program.allowExcessArguments(false);

// Create a subcommand
const sub = program.command('sub');

// The subcommand doesn't inherit the allowExcessArguments setting
// It uses its own default value instead of the parent's configuration
```

### Expected behavior

Subcommands should inherit the `allowExcessArguments` configuration from their parent command, just like other settings such as `_showHelpAfterError`, `_helpConfiguration`, etc.

### Additional context

Other inherited settings like `_exitCallback`, `_storeOptionsAsProperties`, and `_showHelpAfterError` work correctly, but `_allowExcessArguments` doesn't seem to propagate to subcommands.

---
Repository: /testbed
