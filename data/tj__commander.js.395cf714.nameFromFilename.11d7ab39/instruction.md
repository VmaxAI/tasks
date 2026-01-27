# Bug Report

### Describe the bug

The `nameFromFilename()` method is producing incorrect command names. Instead of extracting the actual filename without extension, it seems to be using the directory name.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

// Using a file path like '/usr/local/bin/my-command.js'
program.nameFromFilename('/usr/local/bin/my-command.js');

console.log(program.name()); // Expected: 'my-command', but getting 'bin' instead
```

### Expected behavior

When calling `nameFromFilename()` with a file path, it should extract the filename (without extension) and use that as the command name. For example:
- `/path/to/my-app.js` should result in command name `my-app`
- `./scripts/deploy.js` should result in command name `deploy`

Instead, it appears to be extracting the parent directory name.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
