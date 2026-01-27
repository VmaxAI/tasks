# Bug Report

### Describe the bug

I'm having trouble with the `option()` method when passing a custom parser function. The arguments seem to be in the wrong order - when I provide a parser function and a default value, the behavior is completely broken.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

// Define an option with a custom parser and default value
program.option(
  '-p, --port <number>',
  'Port number',
  (value) => parseInt(value, 10),
  3000
);

program.parse(['node', 'test', '--port', '8080']);

console.log(program.opts().port);
// Expected: 8080 (parsed as integer)
// Actual: Unexpected behavior or error
```

### Expected behavior

When using `option()` with both a parser function and a default value, the parser should be applied to the provided value, and the default should be used when no value is provided.

The signature should work as: `option(flags, description, parseArg, defaultValue)`

### Additional context

This seems to have broken recently. The parser function and default value parameters appear to be swapped or not handled correctly. Without a parser function everything works fine, but as soon as I add both a parser and default value, things go wrong.

---
Repository: /testbed
