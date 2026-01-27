# Bug Report

### Describe the bug

I'm encountering unexpected behavior with argument validation in commander.js. When I pass the correct number of arguments to a command, it's throwing an "error: too many arguments" error even though the argument count matches what's expected.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .command('deploy')
  .argument('<env>', 'environment')
  .argument('<version>', 'version number')
  .action((env, version) => {
    console.log(`Deploying ${version} to ${env}`);
  });

// This should work but throws an error
program.parse(['node', 'script.js', 'deploy', 'production', '1.0.0']);
```

### Expected behavior

The command should execute successfully when provided with exactly the number of arguments it expects. The error message about "too many arguments" should only appear when there are actually more arguments than expected.

### System Info
- commander.js version: latest
- Node version: 18.x

This is blocking our deployment scripts. Any help would be appreciated!

---
Repository: /testbed
