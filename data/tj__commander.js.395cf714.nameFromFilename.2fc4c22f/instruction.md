# Bug Report

### Describe the bug

The `nameFromFilename()` method is producing incorrect command names. When I pass a filename to extract the command name, it's returning the directory path instead of the actual base filename without extension.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

// Try to set name from a file path
program.nameFromFilename('/usr/local/bin/my-command.js');

console.log(program.name()); 
// Expected: 'my-command'
// Actual: '/usr/local/bin' (or similar directory path)
```

### Steps to reproduce:
1. Create a new Command instance
2. Call `nameFromFilename()` with a file path like `'/path/to/script.js'`
3. Check the resulting command name with `name()`
4. The name is set to the directory path instead of 'script'

### Expected behavior

The command name should be extracted from the filename without the extension. For example:
- `/usr/bin/my-app.js` should produce `'my-app'`
- `./scripts/deploy.js` should produce `'deploy'`
- `command.js` should produce `'command'`

### System Info
- commander version: latest
- Node.js version: 18.x

This seems like a regression as this method was working fine before. Any help would be appreciated!

---
Repository: /testbed
