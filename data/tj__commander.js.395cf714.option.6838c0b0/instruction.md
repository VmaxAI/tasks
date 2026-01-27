# Bug Report

### Describe the bug

When using the `option()` method with a custom parser function, the arguments are being passed in the wrong order internally. This causes the parser function to not be applied correctly, and instead the parser gets treated as the default value.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

function parseInteger(value) {
  return parseInt(value);
}

program
  .option('-p, --port <number>', 'port number', parseInteger, 3000);

program.parse(['node', 'test', '--port', '8080']);

console.log(program.opts().port);
// Expected: 8080 (as a number)
// Actual: function parseInteger() { ... } or unexpected behavior
```

### Expected behavior

The custom parser function should be invoked to parse the option value, and the default value should be used when the option is not provided. The parsed value should be the result of calling `parseInteger('8080')` which is `8080` as a number.

### System Info

- commander version: latest
- Node.js version: v18.x

---
Repository: /testbed
