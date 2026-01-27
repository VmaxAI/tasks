# Bug Report

### Describe the bug

When using `addHelpOption()` to customize the help option, the method doesn't return the command instance for chaining. Instead, it returns the option object itself, which breaks the fluent API pattern used throughout the library.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

// This should allow chaining but doesn't work
program
  .addHelpOption(new Option('-h, --help', 'display help'))
  .version('1.0.0')  // TypeError: program.addHelpOption(...).version is not a function
  .parse();
```

### Expected behavior

The `addHelpOption()` method should return the command instance (like other methods such as `option()`, `argument()`, etc.) to allow method chaining:

```js
program
  .addHelpOption(new Option('-h, --help', 'display help'))
  .version('1.0.0')
  .parse();  // Should work
```

### System Info
- commander version: latest
- Node.js version: v18.x

---
Repository: /testbed
