# Bug Report

### Describe the bug

When displaying help text for command options, leading/trailing whitespace in option descriptions is being preserved instead of being trimmed. This causes inconsistent formatting in the help output, especially when option descriptions have extra spaces at the beginning or end.

### Reproduction

```js
program
  .option('-f, --format <type>', '  output format  ')
  .option('-v, --verbose', 'enable verbose mode');

program.parse();
```

When running with `--help`, the description for the `--format` option displays with the extra spaces intact, making the help text look misaligned compared to other options.

### Expected behavior

Option descriptions should have leading and trailing whitespace trimmed automatically to ensure consistent formatting in the help output. All option descriptions should align properly regardless of whether the source strings contain extra whitespace.

### System Info
- Node version: 18.x
- OS: macOS

---
Repository: /testbed
