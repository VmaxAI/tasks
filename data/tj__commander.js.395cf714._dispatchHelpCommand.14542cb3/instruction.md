# Bug Report

### Describe the bug

When invoking the help command without specifying a subcommand name, the help output is not displayed. Instead of showing the main command help, nothing happens or the behavior is incorrect.

### Reproduction

```js
const program = new Command();

program
  .command('subcommand')
  .description('A subcommand');

// Try to display help for the main command
program.parse(['node', 'script', 'help']);
```

### Expected behavior

When running `help` without a subcommand name, it should display the help information for the main command. Currently, the help is only shown when a subcommand name is provided, which is the opposite of what should happen.

### Additional context

This seems to affect the logic that determines when to show help - the condition appears to be inverted. The help should be displayed when NO subcommand is specified, not when one IS specified.

---
Repository: /testbed
