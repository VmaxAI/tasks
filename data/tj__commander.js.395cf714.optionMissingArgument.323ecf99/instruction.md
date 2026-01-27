# Bug Report

### Describe the bug

When an option is missing its required argument, the error message and handling seems broken. The error is no longer being properly thrown, and instead of showing the option flags (like `-f, --file`), it's only showing the option name.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-f, --file <path>', 'file to process')
  .parse();

// Run with: node script.js -f
// (missing the required argument after -f)
```

### Expected behavior

1. Should throw an error (not just emit an event)
2. Error message should display the full option flags (e.g., `-f, --file`) instead of just the option name

When I run my CLI tool with an option that requires an argument but don't provide one, the program doesn't exit with an error like it used to. It seems like the error handling changed and now it's just emitting an event instead of actually throwing the error.

### System Info
- commander.js version: latest
- Node.js: v18.x

---
Repository: /testbed
