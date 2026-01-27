# Bug Report

### Describe the bug

The help text formatting for global options is completely broken. When displaying help for commands with global options, the column alignment is all messed up - some option descriptions are squished together while there's way too much space in other places.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('-d, --debug', 'output extra debugging')
  .option('-s, --small', 'small pizza size')
  .option('-p, --pizza-type <type>', 'flavour of pizza');

program
  .command('serve')
  .description('serve the application')
  .option('-P, --port <port>', 'port to listen on')
  .action(() => {});

program.parse(['node', 'test', 'serve', '--help']);
```

### Expected behavior

The help output should have consistent column widths with proper alignment. The option terms and their descriptions should be nicely aligned in columns like they used to be.

Instead, the formatting looks really weird - the columns are way too narrow and the text doesn't line up properly.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
