# Bug Report

### Describe the bug

When using nested commands with global options, `getOptionValueSourceWithGlobals()` returns the wrong source priority. It seems like the method is returning the source from the first command in the hierarchy that has the option defined, instead of prioritizing global options over local ones.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('-d, --debug', 'enable debug mode');

program
  .command('serve')
  .option('-d, --debug', 'local debug option')
  .action((options, cmd) => {
    console.log('Value source:', cmd.getOptionValueSourceWithGlobals('debug'));
  });

// When running with global flag:
// node app.js --debug serve
// Expected: should return source from parent/global command
// Actual: returns source from local command
```

### Expected behavior

The method should prioritize global option sources over local ones (as the comment in the code says "global overwrites local"), but it's doing the opposite - it returns the first source it finds when traversing from child to ancestors.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
