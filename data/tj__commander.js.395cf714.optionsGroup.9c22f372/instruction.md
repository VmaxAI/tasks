# Bug Report

### Describe the bug

When calling `optionsGroup()` with a heading parameter, the method is returning the heading string instead of the Command instance, which breaks method chaining.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// This should work but throws an error
program
  .optionsGroup('Global Options')
  .option('-d, --debug', 'enable debug mode')
  .option('-v, --verbose', 'verbose output');
```

The error occurs because `optionsGroup()` returns a string instead of the Command object, so the subsequent `.option()` call fails.

### Expected behavior

The `optionsGroup()` method should return the Command instance (like other builder methods) to allow method chaining. This was working in previous versions.

### Workaround

Currently have to split the chain:
```js
program.optionsGroup('Global Options');
program.option('-d, --debug', 'enable debug mode');
program.option('-v, --verbose', 'verbose output');
```

But this defeats the purpose of the fluent API design.

---
Repository: /testbed
