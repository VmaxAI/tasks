# Bug Report

### Describe the bug

I'm encountering an issue with variadic options where they're not being recognized correctly. When I define an option with a variadic value pattern like `--option <value...>`, it's not being treated as variadic anymore.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-n, --numbers <nums...>', 'list of numbers');

program.parse(['node', 'test', '--numbers', '1', '2', '3']);

// The option should accept multiple values but doesn't work as expected
console.log(program.opts());
```

Expected the option to be recognized as variadic and collect all the values, but it seems like the variadic detection is broken.

### Additional context

This appears to have started happening recently. Options with patterns like `<value...>` or `[value...]` should be detected as variadic but they're not being handled properly anymore.

---
Repository: /testbed
