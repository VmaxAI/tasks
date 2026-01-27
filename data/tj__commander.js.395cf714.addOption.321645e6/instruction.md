# Bug Report

### Describe the bug

After a recent update, options with default values are not being properly initialized. When I define an option with a default value, the default isn't being set on the command instance, causing the option to be undefined when accessed before being explicitly set.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('-p, --port <number>', 'port number', '3000')
  .parse(process.argv);

console.log(program.opts().port);
// Expected: '3000'
// Actual: undefined
```

Also seeing issues with negated options (--no-* flags). The default behavior seems broken:

```js
const program = new Command();

program
  .option('--no-color', 'disable color output')
  .parse([]);

console.log(program.opts().color);
// Expected: true (default for negated options)
// Actual: undefined
```

### Expected behavior

Options should have their default values set automatically when the command is created. Negated options should default to `true` unless explicitly disabled.

### System Info
- commander version: latest
- Node.js: v18.x

---
Repository: /testbed
