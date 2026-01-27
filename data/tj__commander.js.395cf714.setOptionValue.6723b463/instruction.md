# Bug Report

### Describe the bug

I'm experiencing an issue with `setOptionValue()` where setting option values doesn't work as expected. When I try to set an option value using this method, the behavior is incorrect and the values don't seem to be stored properly.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-p, --port <number>', 'port number')
  .parse();

// Try to manually set an option value
program.setOptionValue('port', 3000);

console.log(program.opts().port); // Expected: 3000, but getting unexpected behavior
```

### Expected behavior

When calling `setOptionValue('port', 3000)`, the option should be set correctly and `program.opts().port` should return `3000`.

### System Info
- commander version: latest
- Node version: 18.x

This seems to have broken recently. The method used to work fine in earlier versions.

---
Repository: /testbed
