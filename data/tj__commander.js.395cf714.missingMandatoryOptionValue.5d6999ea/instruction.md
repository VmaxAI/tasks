# Bug Report

### Describe the bug

When a required option is missing, the error message displays the option's internal name instead of its flags. This makes it harder for users to understand which option they need to provide.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .requiredOption('-u, --username <name>', 'username is required')
  .parse(process.argv);
```

When running this without providing the `--username` option, the error message shows:
```
error: required option 'username' not specified
```

### Expected behavior

The error message should display the flags (e.g., `-u, --username <name>`) instead of just the option name (`username`), so users know exactly what syntax to use when providing the option.

Expected error message:
```
error: required option '-u, --username <name>' not specified
```

This makes it much clearer what the user needs to type on the command line.

---
Repository: /testbed
