# Bug Report

### Describe the bug

The `configureHelp()` method is not working as expected. When I try to set a help configuration and then chain additional commands, it returns the configuration object instead of the command instance. This breaks method chaining.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// This should allow chaining but doesn't work
program
  .configureHelp({ sortSubcommands: true })
  .version('1.0.0')
  .parse(process.argv);
```

When running this code, I get an error like `TypeError: program.configureHelp(...).version is not a function` because `configureHelp()` is returning the configuration object instead of the command instance.

Also, trying to retrieve the current configuration doesn't work:

```js
const config = program.configureHelp();
console.log(config); // Expected: current help configuration, Actual: undefined
```

### Expected behavior

- When called with a configuration object, `configureHelp()` should return the command instance to allow method chaining
- When called without arguments, it should return the current help configuration

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
