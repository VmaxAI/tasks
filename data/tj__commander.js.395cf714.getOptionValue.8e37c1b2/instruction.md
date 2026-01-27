# Bug Report

### Describe the bug

I'm experiencing an issue where `getOptionValue()` is returning `undefined` for valid option keys. The method seems to be looking up values incorrectly, causing options that were set to not be retrievable.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-p, --port <number>', 'port number')
  .parse(['node', 'test', '--port', '3000']);

console.log(program.getOptionValue('port'));
// Expected: '3000'
// Actual: undefined
```

### Expected behavior

`getOptionValue('port')` should return the value `'3000'` that was passed via the command line arguments. The method should correctly retrieve option values using their key names.

### System Info
- commander.js version: latest
- Node.js version: 18.x

This seems to have broken recently - the same code was working fine before. Any help would be appreciated!

---
Repository: /testbed
