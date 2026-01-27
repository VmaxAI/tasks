# Bug Report

### Describe the bug

I'm experiencing an issue with variadic options when using the `variadic()` method. When I provide multiple values for a variadic option, they're being concatenated in the wrong order - the new values appear before the previous ones instead of after them.

### Reproduction

```js
const program = new Command();
program
  .option('-n, --number <values...>', 'numbers')
  .action((options) => {
    console.log(options.number);
  });

// Parse multiple times or with multiple values
program.parse(['-n', '1', '-n', '2'], { from: 'user' });
```

### Expected behavior

When accumulating variadic option values, the new values should be appended to the end of the existing array. For example, if I call the option with `1` first and then `2`, I should get `[1, 2]`, not `[2, 1]`.

The order matters for my use case where I'm processing items sequentially based on the order they were specified on the command line.

### System Info
- Node version: 18.x
- commander.js version: latest

---
Repository: /testbed
