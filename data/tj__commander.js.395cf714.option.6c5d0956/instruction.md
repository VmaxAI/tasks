# Bug Report

### Describe the bug

I'm experiencing an issue with the `.option()` method where the option flags and descriptions seem to be getting mixed up. When I define command options, the behavior is completely broken - options aren't being parsed correctly and the help text shows garbled information.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-d, --debug', 'enable debug mode')
  .option('-v, --verbose', 'verbose output')
  .parse(process.argv);

console.log(program.opts());
```

When running this with `-d` flag, the option doesn't work as expected. The help output also appears incorrect with the flags and descriptions not displaying properly.

### Expected behavior

The options should be parsed correctly with their flags and descriptions in the right place. The help text should show:
```
-d, --debug      enable debug mode
-v, --verbose    verbose output
```

And using the flags should properly set the option values.

### System Info
- commander version: latest
- Node.js version: 18.x

This seems to have broken recently, possibly after a recent update. Any help would be appreciated!

---
Repository: /testbed
