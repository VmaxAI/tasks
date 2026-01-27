# Bug Report

### Describe the bug

I'm having an issue with the `allowExcessArguments()` method. When I call it with `true` to allow excess arguments, it actually seems to disallow them, and when I call it with `false` to disallow excess arguments, it allows them instead. The behavior is completely inverted from what's expected.

Also, the method is now returning a boolean value instead of the command instance, which breaks method chaining.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .argument('<file>')
  .allowExcessArguments(true)  // Should allow excess args
  .action((file, options, cmd) => {
    console.log('file:', file);
  });

// This should work but throws an error about excess arguments
program.parse(['node', 'script.js', 'file.txt', 'extra1', 'extra2']);
```

Also, method chaining doesn't work anymore:

```js
program
  .argument('<file>')
  .allowExcessArguments(true)
  .action(() => {})  // TypeError: Cannot read property 'action' of undefined
```

### Expected behavior

- `allowExcessArguments(true)` should allow excess arguments to be passed without error
- `allowExcessArguments(false)` should disallow excess arguments and throw an error when they're provided
- The method should return the command instance for chaining, not a boolean value

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
