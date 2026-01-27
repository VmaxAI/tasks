# Bug Report

### Describe the bug

I'm trying to set default values for command line options using the `.default()` method, but it seems to have stopped working completely. When I try to call `.default()` on an option, I get an error saying that the method doesn't exist or is not a function.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-p, --port <number>', 'port number')
  .default(3000, 'default port');

program.parse();
```

When running this code, I get a TypeError indicating that `.default()` is not available on the option.

### Expected behavior

The `.default()` method should set a default value for the option, so that if the user doesn't provide the `--port` flag, it defaults to 3000. This was working fine before.

### Additional context

This is breaking my CLI application as I rely heavily on default values for optional configuration parameters. The method seems to have been replaced with something else or removed entirely.

---
Repository: /testbed
