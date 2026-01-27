# Bug Report

### Describe the bug

The `addHelpText()` method is not displaying custom help text when calling help on commands. I've added help text using `addHelpText('before', 'My custom help')` but nothing shows up when I run `--help`.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .name('myapp')
  .description('My application')
  .addHelpText('before', 'This is custom text that should appear before help');

program.parse();
```

When running with `--help` flag, the custom help text doesn't appear at all. I've tried with different positions ('beforeAll', 'after', 'afterAll') and none of them work.

### Expected behavior

The custom help text should be displayed in the help output at the specified position. For example, with `addHelpText('before', 'Custom text')`, the text should appear before the main help content.

### Additional context

This was working fine in previous versions. I recently updated and now the help text just doesn't show up anymore. The command itself works fine, just the custom help text is missing from the output.

---
Repository: /testbed
