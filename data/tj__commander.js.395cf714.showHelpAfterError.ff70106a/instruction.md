# Bug Report

### Describe the bug

When calling `showHelpAfterError()` with a string argument, the help text is not being displayed after errors as expected. The method seems to be ignoring string values and not properly setting the help display behavior.

### Reproduction

```js
const program = new Command();

// This should enable help display with custom message
program.showHelpAfterError('Try --help for more information');

// Trigger an error (e.g., invalid option)
// Expected: Error message followed by the custom help text
// Actual: Help text is not displayed
```

Also noticed that passing boolean values might not work as intended:

```js
program.showHelpAfterError(true);
// Help should be shown after errors, but behavior seems inconsistent
```

### Expected behavior

- When passing a string to `showHelpAfterError()`, it should display that string after error messages
- When passing `true`, it should display default help after errors
- When passing `false`, it should not display help after errors

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
