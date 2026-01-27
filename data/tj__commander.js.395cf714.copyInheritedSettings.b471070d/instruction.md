# Bug Report

### Describe the bug

When creating subcommands, the `showHelpAfterError` configuration is not being inherited from the parent command. Instead, the subcommand retains its own default value rather than copying the parent's setting.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();
program.showHelpAfterError();

const subcommand = program.command('sub');

// The subcommand should have inherited showHelpAfterError from parent
// but it doesn't work as expected
```

Steps to reproduce:
1. Create a parent command with `showHelpAfterError()` enabled
2. Add a subcommand to the parent
3. Trigger an error in the subcommand
4. Notice that help is not displayed after the error, even though the parent has this setting enabled

### Expected behavior

Subcommands should inherit the `showHelpAfterError` setting from their parent command. When a parent command has `showHelpAfterError` enabled, all child commands should automatically display help after errors unless explicitly overridden.

This behavior should be consistent with how other settings like `_allowExcessArguments` and `_showSuggestionAfterError` are inherited from parent to child commands.

---
Repository: /testbed
