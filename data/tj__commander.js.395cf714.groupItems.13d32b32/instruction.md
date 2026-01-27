# Bug Report

### Describe the bug
When using the help system with grouped commands/options, items are appearing duplicated in the help output. Each item shows up twice in its group instead of appearing only once.

### Reproduction
```js
// Create a command with grouped options
const program = new Command();
program
  .option('-a, --alpha', 'alpha option', { group: 'group1' })
  .option('-b, --beta', 'beta option', { group: 'group1' })
  .option('-c, --charlie', 'charlie option', { group: 'group2' });

// Display help
program.help();
```

### Expected behavior
Each option should appear exactly once in its respective group in the help output.

### Actual behavior
Options are duplicated - they appear twice in the same group when the help text is generated.

This seems to have started happening recently. The help output used to show each item only once per group, but now everything is doubled up which makes the help text confusing and harder to read.

---
Repository: /testbed
