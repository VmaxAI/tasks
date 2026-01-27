# Bug Report

### Describe the bug

I'm getting an error thrown when trying to use executable subcommands, but the error message doesn't make sense. It says the executable file doesn't exist even when it actually does exist on the filesystem.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

// Create a subcommand with an executable file that exists
program
  .command('deploy', 'deploy description')
  .executableDir('./bin');

program.parse(process.argv);
```

When I run this with a valid executable file at `./bin/myprogram-deploy`, it throws an error saying the file doesn't exist, but I can verify the file is there.

Also noticed the error message itself looks wrong - it mentions "no directory for search" when I actually provided a directory, and says "searched for local subcommand" when I didn't provide one.

### Expected behavior

The command should execute the subcommand without throwing an error when the executable file exists. The error should only be thrown when the file is actually missing.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
