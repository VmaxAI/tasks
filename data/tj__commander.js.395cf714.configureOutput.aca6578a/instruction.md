# Bug Report

### Describe the bug

I'm having an issue with `configureOutput()` where passing `undefined` doesn't return the current configuration anymore. It seems like the method now treats `undefined` as a valid configuration object and tries to merge it, which overwrites my existing settings.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// Set initial output configuration
program.configureOutput({
  writeOut: (str) => console.log('Custom out:', str),
  writeErr: (str) => console.error('Custom err:', str)
});

// Try to get current configuration
const config = program.configureOutput(undefined);

// config is now undefined instead of returning the configuration object
console.log(config); // Expected: { writeOut: [Function], writeErr: [Function] }
                     // Actual: undefined
```

Also, when I set a configuration and then call `configureOutput()` again with a new partial configuration, my previous settings get completely replaced instead of being merged:

```js
program.configureOutput({
  writeOut: (str) => console.log('OUT:', str),
  writeErr: (str) => console.error('ERR:', str),
  outputError: (str) => console.error('ERROR:', str)
});

// Add another property
program.configureOutput({
  getOutHelpWidth: () => 80
});

// Now writeOut, writeErr, and outputError are gone!
```

### Expected behavior

- Calling `configureOutput(undefined)` should return the current output configuration
- New configurations should be merged with existing ones, not replace them completely

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
