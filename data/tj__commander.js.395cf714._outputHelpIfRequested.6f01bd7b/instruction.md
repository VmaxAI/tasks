# Bug Report

### Describe the bug

I'm experiencing an issue with the help option behavior in commander. When I pass the help flag (`--help` or `-h`) along with other arguments, the help is not being displayed. It seems like the help option is only triggered when ALL arguments are help flags, which doesn't make sense for normal CLI usage.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-n, --name <name>', 'specify name')
  .option('-a, --age <age>', 'specify age');

program.parse(['node', 'script.js', '--help', '--name', 'John']);
```

### Expected behavior

When `--help` is included in the arguments, the help should be displayed and the program should exit, regardless of what other arguments are present. The typical CLI behavior is that help takes precedence and shows usage information immediately.

Currently, if I pass `--help` along with any other argument, nothing happens and the program continues execution instead of showing the help text.

### System Info
- commander.js version: latest
- Node version: 18.x

---
Repository: /testbed
