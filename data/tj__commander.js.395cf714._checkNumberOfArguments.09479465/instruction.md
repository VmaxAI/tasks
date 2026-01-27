# Bug Report

### Describe the bug

I'm encountering an issue with argument validation in commands. When I define a command with required arguments, the validation seems to be checking the wrong argument positions, causing incorrect "missing argument" errors even when all required arguments are provided.

### Reproduction

```js
const program = require('commander');

program
  .command('deploy')
  .argument('<environment>', 'deployment environment')
  .argument('<version>', 'version to deploy')
  .action((environment, version) => {
    console.log(`Deploying ${version} to ${environment}`);
  });

program.parse(['node', 'script.js', 'deploy', 'production', 'v1.2.3']);
```

When running this code, I get a "missing argument" error for 'environment' even though both 'production' and 'v1.2.3' are clearly provided.

### Expected behavior

The command should execute successfully without any validation errors since all required arguments are present. The action callback should receive the correct values for both parameters.

### Additional context

This seems to have started recently. I'm not sure if it's related to how arguments are being indexed or validated internally, but the error message doesn't match the actual state of the provided arguments.

---
Repository: /testbed
