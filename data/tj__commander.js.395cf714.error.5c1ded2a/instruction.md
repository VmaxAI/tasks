# Bug Report

### Describe the bug

I'm encountering an issue with the `showHelpAfterError` feature. When I set `showHelpAfterError` to a string value (like a custom help message), it doesn't display the help text correctly. Instead, it seems to be checking the condition in the wrong order.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .showHelpAfterError('(add --help for additional information)')
  .argument('<file>')
  .action((file) => {
    console.log('file:', file);
  });

// When an error occurs (e.g., missing required argument)
// Expected: Should show the custom string message
// Actual: The behavior is incorrect
```

When I trigger an error by not providing the required argument, the help text doesn't show up as expected. It seems like when `showHelpAfterError` is set to a string, it's not being handled properly.

### Expected behavior

When `showHelpAfterError` is set to:
- `true` - should display the full help text
- A custom string - should display that custom string after the error message

The custom string message should be displayed after error messages to guide users, but currently this doesn't work as intended.

### Additional context

This affects error handling in CLI applications where you want to show a brief hint to users about how to get more information when they make a mistake with command arguments or options.

---
Repository: /testbed
