# Bug Report

### Describe the bug

I'm experiencing an issue with custom option parsing when using a RegExp as the coercion function. The parsed value returned is not what I expected - instead of getting the matched string value, I'm receiving the entire match object/array.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('-p, --port <number>', 'port number', /^\d+$/)
  .parse(['node', 'test', '--port', '3000']);

const options = program.opts();
console.log(options.port);
// Expected: '3000'
// Actual: Match object/array instead of the string value
```

### Expected behavior

When using a RegExp for option coercion, the matched string value should be returned (e.g., `'3000'`), not the match object/array. This is how it worked previously and is the expected behavior for simple value extraction.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
