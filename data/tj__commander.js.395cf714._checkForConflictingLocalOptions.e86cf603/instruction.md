# Bug Report

### Describe the bug

When using options with `conflictsWith` configuration, the conflict detection is not working properly when multiple options are defined that conflict with the same option. Only the first conflicting option is being detected and reported.

### Reproduction

```js
const program = new Command();

program
  .option('-a, --option-a', 'First option')
  .option('-b, --option-b', 'Second option')
  .option('-c, --option-c', 'Third option')
  .conflictsWith(['option-a', 'option-b']);

// Using multiple conflicting options together
program.parse(['node', 'test', '--option-a', '--option-b', '--option-c']);
```

In this scenario, when `--option-c` is used together with both `--option-a` and `--option-b`, only one of the conflicts is detected instead of reporting all conflicting options.

### Expected behavior

All conflicting options should be detected and reported when multiple options that conflict with each other are used together. The error message should indicate all the conflicts, not just the first one found.

### System Info
- Node version: 18.x
- Commander.js version: latest

---
Repository: /testbed
