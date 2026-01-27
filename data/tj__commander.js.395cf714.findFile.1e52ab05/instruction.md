# Bug Report

### Describe the bug

When using `executableFile()` with a filename that has a source extension (like `.js`, `.ts`, `.mjs`, etc.), the command fails to locate the file even when it exists in the expected directory.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .command('serve')
  .executableFile('serve-command.js')
  .description('Run serve command');

program.parse();
```

If I have a file `serve-command.js` in my project directory and try to run:
```bash
node myprogram.js serve
```

The executable file is not found, even though it exists at the correct path.

### Expected behavior

The command should locate and execute `serve-command.js` when it exists in the project directory. Files with source extensions should be found just like files without extensions.

### System Info
- commander version: latest
- Node.js version: v18.x
- OS: macOS

This seems to have started happening recently. The file lookup logic appears to be checking for extensions incorrectly when the base filename already includes a source extension.

---
Repository: /testbed
