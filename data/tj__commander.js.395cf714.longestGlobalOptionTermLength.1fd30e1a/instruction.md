# Bug Report

### Describe the bug

The help text formatting for global options appears broken. When displaying help for commands with multiple global options, the column width calculation seems incorrect, causing misalignment in the help output.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('-d, --debug', 'output extra debugging')
  .option('-s, --small', 'small pizza size')
  .option('-p, --pizza-type <type>', 'flavour of pizza');

program
  .command('order')
  .description('order a pizza')
  .action(() => {});

program.parse();
```

When running with `--help`, the global options section doesn't align properly. It looks like the column widths are being calculated incorrectly, possibly using the shortest option term instead of the longest.

### Expected behavior

The help output should display all global options with proper alignment, with columns sized based on the longest option term to ensure everything lines up nicely.

### System Info
- commander.js version: latest
- Node version: 18.x

---
Repository: /testbed
