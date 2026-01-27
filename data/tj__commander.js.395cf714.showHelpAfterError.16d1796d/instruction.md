# Bug Report

### Describe the bug

When calling `showHelpAfterError()` with a string argument, the behavior is inverted. Passing a string value results in help NOT being displayed after errors, which is the opposite of what should happen.

### Reproduction

```js
const program = new Command();

// This should enable help display with custom message
program.showHelpAfterError('Use --help for more information');

// But after an error occurs, help is not shown
// The string argument is being treated incorrectly
```

### Expected behavior

When `showHelpAfterError()` is called with a string argument, it should:
1. Enable help display after errors
2. Use the provided string as the help message

Currently, passing a string disables help display instead of enabling it with a custom message.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
