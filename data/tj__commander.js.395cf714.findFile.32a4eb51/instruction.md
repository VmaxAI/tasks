# Bug Report

### Describe the bug

When using `executableFile()` with source file extensions (.js, .ts, etc.), the command execution fails because the file extension is not being appended to the resolved path.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .command('run')
  .executableFile('scripts/my-script.js')
  .action(() => {});

program.parse();
```

When the executable file is `scripts/my-script.js` (or any source file with extension like .ts, .mjs, .cjs), the program tries to execute a path without the extension appended, causing the execution to fail.

### Expected behavior

The program should correctly resolve and execute files with source extensions. When a file like `my-script.js` exists, it should be found and executed with the full path including the `.js` extension.

### System Info
- commander version: latest
- Node.js version: 18.x
- OS: Linux/macOS

---
Repository: /testbed
