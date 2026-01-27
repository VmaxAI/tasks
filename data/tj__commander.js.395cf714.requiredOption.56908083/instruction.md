# Bug Report

### Describe the bug

I'm experiencing an issue with `requiredOption()` where it's not actually requiring the option to be provided. When I define a required option and run my CLI without providing it, the program continues execution instead of throwing an error about the missing required option.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .requiredOption('-p, --port <number>', 'Port number')
  .parse(process.argv);

console.log('Program executed successfully');
```

Run without providing the required option:
```bash
node myapp.js
```

### Expected behavior

The program should exit with an error message indicating that the required option `-p, --port` was not provided. Instead, it just continues execution as if the option was optional.

### Additional context

This seems like a regression - required options were working correctly in previous versions. Now they behave the same as regular optional options.

---
Repository: /testbed
