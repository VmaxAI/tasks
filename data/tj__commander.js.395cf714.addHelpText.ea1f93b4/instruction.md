# Bug Report

### Describe the bug

I'm having issues with `addHelpText()` not displaying custom help text in the correct position. When I try to add help text at different positions like 'before', 'after', or 'afterAll', the text always appears in the same place (at the 'beforeAll' position) regardless of what position I specify.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .name('myapp')
  .description('Test application');

// Try to add help text at different positions
program.addHelpText('before', 'This should appear BEFORE options');
program.addHelpText('after', 'This should appear AFTER options');
program.addHelpText('afterAll', 'This should appear at the very END');

program.parse();
```

When running `node myapp.js --help`, all the custom help text appears at the beginning instead of being positioned correctly. The 'before', 'after', and 'afterAll' text all show up in the 'beforeAll' position.

Also noticed that sometimes the help text doesn't show up at all, even when it should be displayed.

### Expected behavior

- Text added with position 'before' should appear before the options
- Text added with position 'after' should appear after the options  
- Text added with position 'afterAll' should appear at the very end
- Each position should work independently and display the text in the correct location

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
