# Bug Report

### Describe the bug

The `showSuggestionAfterError()` method is not working as expected. When I set it to `true`, suggestions are not displayed after errors, and when I set it to `false`, suggestions ARE displayed. The behavior seems to be inverted from what the documentation indicates.

### Reproduction

```js
const program = new Command();

program
  .showSuggestionAfterError(true)
  .command('test')
  .action(() => {});

// Try running with an invalid command
// Expected: suggestions should be shown
// Actual: no suggestions are displayed
```

Conversely:

```js
program.showSuggestionAfterError(false);

// Try running with an invalid command  
// Expected: no suggestions should be shown
// Actual: suggestions ARE displayed
```

### Expected behavior

When `showSuggestionAfterError(true)` is called, the program should display command suggestions after an error occurs. When `showSuggestionAfterError(false)` is called, suggestions should be suppressed.

Currently the behavior is backwards - passing `true` hides suggestions and passing `false` shows them.

### Additional context

This is affecting error handling in my CLI application where I want to show helpful suggestions to users when they mistype commands.

---
Repository: /testbed
