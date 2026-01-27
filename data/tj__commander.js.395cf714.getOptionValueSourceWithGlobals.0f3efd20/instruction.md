# Bug Report

### Describe the bug

I'm experiencing an issue with `getOptionValueSourceWithGlobals()` where it's not correctly returning the option value source when dealing with command hierarchies. The method seems to be returning `undefined` even when a valid source exists in the command chain.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();
program
  .option('-d, --debug', 'enable debug mode');

const subCommand = program
  .command('sub')
  .option('-v, --verbose', 'verbose output');

// Set option on parent command
program.parse(['node', 'test', '--debug', 'sub']);

// Try to get the source - returns undefined instead of expected value
const source = subCommand.getOptionValueSourceWithGlobals('debug');
console.log(source); // Expected: 'cli' or similar, Actual: undefined
```

### Expected behavior

When an option is set on a parent command, `getOptionValueSourceWithGlobals()` should traverse the command hierarchy and return the source where the option was defined (e.g., 'cli', 'env', 'config', etc.). Currently it's returning `undefined` even when the option clearly has a source.

This is breaking my use case where I need to determine whether an option was set via command line, environment variable, or config file across a command hierarchy with global options.

### System Info
- commander.js version: latest
- Node.js version: v18.x

---
Repository: /testbed
