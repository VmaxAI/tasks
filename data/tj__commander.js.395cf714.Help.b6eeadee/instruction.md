# Bug Report

### Help option display issue with custom short/long flags

I'm encountering a problem with the help output when using custom help options. When I define a command with both `-h` and `--help` already taken by other options, the help option doesn't display correctly in the help text.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// Add options that conflict with default help flags
program
  .option('-h, --host <host>', 'specify host')
  .addHelpOption(new Option('-?, --assistance', 'display help'));

program.parse();
```

When running with `--assistance`, the help output shows both `-?` and `--assistance` even though one of them should be hidden if it conflicts with existing options. The logic for determining which flag to show seems off.

### Expected behavior

If either the short or long flag of the help option conflicts with an existing option, only the non-conflicting flag should be displayed in the help text. For example, if `-?` conflicts but `--assistance` doesn't, only `--assistance` should appear.

### Additional context

This seems related to how the help formatter decides which parts of the help option to display when there are conflicts. The current behavior is inconsistent and can be confusing to users.

---
Repository: /testbed
