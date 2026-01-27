# Bug Report

### Describe the bug

I'm experiencing an issue where argument terms in the help output are being truncated unexpectedly. When displaying command-line arguments that are longer than 10 characters, they get cut off and only show the first 10 characters.

### Reproduction

```js
// When generating help text for a command with a long argument name
const argumentName = '<very-long-argument-name>';

// The help output only shows: '<very-long'
// Expected to show the full name: '<very-long-argument-name>'
```

This seems to affect any argument term that exceeds 10 characters in length. The truncation happens silently without any indication that the text has been cut off.

### Expected behavior

Argument terms should be displayed in full in the help text, regardless of their length. Users need to see the complete argument names to understand what parameters to provide.

### Additional context

This is causing confusion in our CLI tool where we have descriptive argument names like `<configuration-file>` and `<destination-path>` that are now showing up as `<configura>` and `<destinatio>` in the help output.

---
Repository: /testbed
