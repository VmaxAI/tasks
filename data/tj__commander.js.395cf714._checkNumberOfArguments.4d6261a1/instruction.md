# Bug Report

### Describe the bug

I'm experiencing an issue where the command parser is incorrectly reporting excess arguments even when the number of arguments matches exactly what's expected. This happens when I define a command with specific arguments and then call it with the correct number of arguments.

### Reproduction

```js
const program = require('commander');

program
  .command('deploy')
  .argument('<source>')
  .argument('<destination>')
  .action((source, destination) => {
    console.log(`Deploying from ${source} to ${destination}`);
  });

program.parse(['node', 'script.js', 'deploy', './src', './dist']);
```

When running this, I get an error about excess arguments even though I'm providing exactly 2 arguments as expected.

### Expected behavior

The command should execute normally without any excess argument errors when the correct number of arguments is provided.

### Additional context

This seems to affect commands with a fixed number of arguments. Commands with variadic arguments (using `...`) might also be affected but I haven't tested that scenario thoroughly.

---
Repository: /testbed
