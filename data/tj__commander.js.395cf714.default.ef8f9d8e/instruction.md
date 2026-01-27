# Bug Report

### Describe the bug

The `default()` method on arguments is not working as expected. When setting a default value for an argument, the actual default value and its description appear to be swapped, and the method doesn't return the correct object for chaining.

### Reproduction

```js
const program = require('commander');

program
  .argument('<file>', 'file to process')
  .argument('[output]', 'output destination')
  .default('stdout', 'standard output')
  .action((file, output) => {
    console.log('Output:', output);
  });

program.parse();
```

When running without providing the optional `output` argument, the default value is set to the description string instead of the actual value. Also, trying to chain additional methods after `.default()` fails because it's not returning the right object.

### Expected behavior

- The first parameter should be used as the default value
- The second parameter should be used as the description
- The method should return the Argument instance to allow method chaining

### System Info
- commander.js version: latest
- Node.js version: v18.x

---
Repository: /testbed
