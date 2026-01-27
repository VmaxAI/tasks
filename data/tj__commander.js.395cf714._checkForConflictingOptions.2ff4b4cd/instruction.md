# Bug Report

### Describe the bug

I'm experiencing an issue with conflicting option detection in command hierarchies. When I have a parent command with options and create a subcommand, the parent command's options are no longer being validated for conflicts. It seems like the conflict checking is skipping the root command entirely.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// Add conflicting options to parent command
program
  .option('-d, --debug', 'enable debug mode')
  .option('-d, --development', 'enable development mode');  // Should conflict with --debug

program
  .command('sub')
  .option('-v, --verbose', 'verbose output')
  .action(() => {
    console.log('subcommand executed');
  });

// The conflicting options on the parent command are not detected
program.parse(process.argv);
```

### Expected behavior

The program should detect that `-d` is used for both `--debug` and `--development` on the parent command and throw an error about conflicting options. The validation should check all commands in the hierarchy including the root command.

### System Info
- commander version: latest
- Node.js: v18.x

---
Repository: /testbed
