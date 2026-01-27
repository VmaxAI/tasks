# Bug Report

### Describe the bug

The `nameFromFilename()` method is not extracting the correct program name from the filename. Instead of getting the base filename without extension, it appears to be doing something completely wrong with the path.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();
program.nameFromFilename('/path/to/my-cli-tool.js');

console.log(program.name()); 
// Expected: 'my-cli-tool'
// Actual: returns something unexpected
```

When I pass a filepath like `/usr/local/bin/my-program.js`, I expect the program name to be set to `my-program`, but instead I'm getting incorrect results.

### Expected behavior

The method should extract just the filename (without path and extension) and set it as the program name. For example:
- `/path/to/script.js` → `script`
- `./my-tool.js` → `my-tool`
- `cli.js` → `cli`

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
