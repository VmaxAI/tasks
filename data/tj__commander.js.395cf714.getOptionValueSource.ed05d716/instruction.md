# Bug Report

### Describe the bug

The `getOptionValueSource()` method is returning incorrect data. Instead of returning the source for a specific option key, it's returning the entire sources object regardless of which key is requested.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-p, --port <number>', 'port number')
  .option('-h, --host <address>', 'host address');

program.parse(['node', 'test', '--port', '3000']);

// Should return the source for 'port' option only
const portSource = program.getOptionValueSource('port');
console.log(portSource); // Returns entire _optionValueSources object instead of just the source for 'port'

// This means you can't actually check the source of individual options
const hostSource = program.getOptionValueSource('host');
console.log(hostSource); // Also returns the entire object, same as portSource
```

### Expected behavior

`getOptionValueSource(key)` should return the value source for the specific option key passed as an argument, not the entire internal sources object. Each call with a different key should return different values.

For example:
- `getOptionValueSource('port')` should return something like `'cli'` or `'default'`
- `getOptionValueSource('host')` should return `undefined` (since it wasn't provided)

Currently both calls return the same object containing all option sources.

---
Repository: /testbed
