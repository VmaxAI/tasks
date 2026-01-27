# Bug Report

### Describe the bug

I'm experiencing an issue with option precedence when using subcommands with global options. It appears that global options are overriding local options instead of the other way around. According to the documentation, local options should take precedence over global options, but this doesn't seem to be working correctly.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-d, --debug', 'enable debug mode');

program
  .command('serve')
  .option('-d, --debug', 'local debug option')
  .action((options) => {
    console.log('Options:', program.optsWithGlobals());
  });

program.parse(['node', 'test', 'serve', '-d']);
```

When running this, the global `-d` option value is being used instead of the local subcommand's `-d` option. The `optsWithGlobals()` method seems to be merging options in the wrong order.

### Expected behavior

Local/subcommand options should override global options when both are defined. The `optsWithGlobals()` method should return options where local values take precedence over global values with the same name.

### Additional context

This is affecting my CLI application where I have different meanings for the same option flag at different command levels. The current behavior makes it impossible to override global options at the subcommand level.

---
Repository: /testbed
