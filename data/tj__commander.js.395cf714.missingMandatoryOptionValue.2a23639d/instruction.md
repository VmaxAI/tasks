# Bug Report

### Describe the bug

When a required option is missing, the error message displays the option name instead of the flags, and the error code is not being set properly. This makes it harder to identify which option is missing, especially when options have different flag formats (short and long versions).

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .requiredOption('-u, --username <name>', 'username is required')
  .parse(process.argv);
```

When running without the required option:
```bash
node app.js
```

The error message shows something like `error: required option 'username' not specified` instead of showing the flags like `-u, --username <name>`.

Also, the error object is missing the `code` property that should be set to `'commander.missingMandatoryOptionValue'`.

### Expected behavior

The error message should display the option flags (e.g., `-u, --username <name>`) rather than just the name, making it clearer how to provide the option. Additionally, the error should include the proper error code for programmatic error handling.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
