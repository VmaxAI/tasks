# Bug Report

### Describe the bug

Help text formatting is broken after recent changes. When displaying help information with long descriptions, the text wrapping behaves incorrectly - lines are breaking at the wrong positions and content is getting cut off or displayed improperly.

Additionally, the help option itself is not showing up correctly in the help output. It seems like the logic for determining when to display the help option has been inverted, causing it to appear when it shouldn't and disappear when it should be visible.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('-v, --verbose', 'enable verbose mode with a very long description that should wrap properly across multiple lines when displayed')
  .option('-d, --debug', 'enable debug output');

program.parse();
```

When running with `--help`, the help text wrapping is incorrect and the help option visibility is wrong.

### Expected behavior

1. Long option descriptions should wrap cleanly at appropriate character boundaries
2. The help option should be displayed correctly in the help output based on whether there are conflicting options
3. Text should maintain proper spacing when wrapping to new lines

### System Info
- Node version: 18.x
- commander.js version: latest

---
Repository: /testbed
