# Bug Report

### Issue with parse() method returning subcommand instead of root command

I've noticed that after parsing commands with subcommands, the `parse()` method is now returning the subcommand instance instead of the root command instance. This breaks method chaining when you expect to work with the root command after parsing.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .command('sub')
  .action(() => {});

const result = program.parse(['node', 'test', 'sub']);

console.log(result === program); // Expected: true, Actual: false
console.log(result.name()); // Prints 'sub' instead of root command name
```

When I call `parse()` and store the result, I expect it to return the root command so I can continue chaining methods or access properties of the main program. Instead, it's returning the subcommand that was invoked.

This is causing issues in my CLI tool where I need to access the root command's configuration after parsing arguments. My code assumes `parse()` returns the command it was called on, which was the previous behavior.

### Expected behavior

The `parse()` method should return the command instance it was called on (the root command), not the subcommand that gets executed. This is important for method chaining and maintaining references to the correct command object.

---
Repository: /testbed
