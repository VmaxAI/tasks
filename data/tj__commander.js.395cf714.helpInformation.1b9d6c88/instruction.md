# Bug Report

### Describe the bug
When using `helpInformation()`, the color stripping logic appears to be inverted. Help text that should have colors is getting stripped, and text that should be plain is being returned with color codes intact.

### Reproduction
```js
const { Command } = require('commander');

const program = new Command();
program
  .name('my-app')
  .description('Test application')
  .option('-d, --debug', 'enable debug mode');

// When colors are enabled, getting plain text instead
const helpWithColors = program.helpInformation({ hasColors: true });
console.log('With colors:', helpWithColors);

// When colors are disabled, getting colored text instead  
const helpWithoutColors = program.helpInformation({ hasColors: false });
console.log('Without colors:', helpWithoutColors);
```

### Expected behavior
- When `hasColors: true` is passed in the context, the help text should contain ANSI color codes
- When `hasColors: false` or colors are disabled, the help text should be plain without any color codes

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
