# Bug Report

### Describe the bug

I'm experiencing an issue where conflicting options are not being detected properly. When I define two options that should conflict with each other, the program doesn't throw an error and allows both options to be used simultaneously.

### Reproduction

```js
const program = new Command();

program
  .option('-a, --option-a', 'First option')
  .option('-b, --option-b', 'Second option')
  .conflictsWith('option-a', 'option-b');

// Both options can be used together without error
program.parse(['-a', '-b']);
```

### Expected behavior

The program should detect that `--option-a` and `--option-b` are conflicting options and throw an error when both are provided together. Instead, both options are accepted and no conflict error is raised.

This seems to have started happening recently. Previously, the conflict detection was working as expected.

---
Repository: /testbed
