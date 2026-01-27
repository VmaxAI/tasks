# Bug Report

### Describe the bug

When using custom help options with both short and long flags, the help text is displaying incorrectly. It seems like the help option visibility logic is inverted - options that should be hidden are being shown, and options that should be visible are being hidden.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('-d, --debug', 'enable debug mode')
  .option('-h, --help', 'display help'); // custom help option

program.parse();
```

When running with `--help`, the help output shows the wrong combination of short/long flags. If you define a custom help option that conflicts with the built-in one, the visibility filtering behaves opposite to what's expected.

### Expected behavior

The help formatter should correctly filter out conflicting options and display only the non-conflicting flags (either short or long form) when there's a conflict with existing command options.

### Additional context

This appears to affect the `visibleOptions` logic in the help formatter. When checking whether to keep the long or short form of a help option, it seems to be doing the opposite of what it should - keeping options when they conflict instead of when they don't conflict.

---
Repository: /testbed
