# Bug Report

### Describe the bug

I'm experiencing an issue where setting option values programmatically doesn't work as expected. When I call `setOptionValue()` to set an option, the key and value appear to be swapped or not stored correctly.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-p, --port <number>', 'port number')
  .option('-h, --host <address>', 'host address');

// Try to set option values programmatically
program.setOptionValue('port', 3000);
program.setOptionValue('host', 'localhost');

console.log(program.opts());
// Expected: { port: 3000, host: 'localhost' }
// Actual: values are not set correctly or swapped
```

### Expected behavior

The option values should be stored correctly with the proper key-value mapping. When I set `port` to `3000`, I expect `program.opts().port` to return `3000`.

### System Info

- commander version: latest
- Node.js version: 18.x

This seems to have broken recently as it was working fine before. Any help would be appreciated!

---
Repository: /testbed
