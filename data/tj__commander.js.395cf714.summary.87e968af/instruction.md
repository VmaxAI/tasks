# Bug Report

### Describe the bug

I'm having trouble retrieving the summary text from a command after setting it. The getter functionality seems to be broken - when I try to get the summary without passing any arguments, it's not returning the stored value.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();
program.summary('This is my command summary');

// This should return 'This is my command summary' but doesn't work
const summaryText = program.summary();
console.log(summaryText); // Expected: 'This is my command summary', Actual: undefined
```

### Expected behavior

When calling `summary()` without arguments, it should return the previously set summary string. The method should work as both a getter and setter like other similar methods in Commander.

### Additional context

This appears to affect the ability to programmatically read back the summary that was set on a command, which is useful for documentation generation and introspection purposes.

---
Repository: /testbed
