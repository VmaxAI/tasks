# Bug Report

### Describe the bug

I'm experiencing strange behavior with the `argRequired()` method. When I call it on an argument, the command parsing fails unexpectedly and my program doesn't work as expected.

### Reproduction

```js
const { Command, Argument } = require('commander');

const program = new Command();

program
  .command('test')
  .addArgument(new Argument('<name>').argRequired())
  .action((name) => {
    console.log('Name:', name);
  });

program.parse();
```

When running this code, the command doesn't behave correctly. It seems like calling `argRequired()` breaks the argument configuration somehow.

### Expected behavior

The `argRequired()` method should mark the argument as required and allow method chaining to continue working normally. The command should execute properly when the required argument is provided.

### Additional context

This used to work fine in previous versions. I noticed the issue after updating to the latest release. It feels like the method is doing something unexpected now.

---
Repository: /testbed
