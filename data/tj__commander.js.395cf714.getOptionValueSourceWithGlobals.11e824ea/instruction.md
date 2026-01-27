# Bug Report

### Describe the bug

When using global options with command inheritance, the option value source is not being resolved correctly. It seems like local option sources are overwriting global ones instead of the other way around.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('-g, --global <value>', 'global option')
  .command('sub')
  .option('-g, --global <value>', 'local option')
  .action((options) => {
    // Check the source of the global option
    const source = program.getOptionValueSourceWithGlobals('global');
    console.log('Option source:', source);
  });

// Run with global option
program.parse(['node', 'test', '--global', 'fromGlobal', 'sub', '--global', 'fromLocal']);
```

### Expected behavior

The method `getOptionValueSourceWithGlobals` should return the global option source when a global option is set, following the documented behavior that "global overwrites local". However, it appears to be returning the local source instead.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
