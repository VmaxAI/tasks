# Bug Report

### Describe the bug

I'm experiencing an issue with options that use the `variadic` or `concat` behavior. When I provide the same option multiple times on the command line, the values aren't being accumulated correctly into an array.

### Reproduction

```js
const { Command, Option } = require('commander');

const program = new Command();
program.addOption(
  new Option('-v, --value <items...>')
    .default([])
);

program.parse(['-v', 'first', '-v', 'second'], { from: 'user' });

console.log(program.opts().value);
// Expected: ['first', 'second']
// Actual: ['first']
```

When I specify the option multiple times, only the first value is kept instead of concatenating all values together.

### Expected behavior

Multiple invocations of the same option should accumulate values into an array. The second call should append to the existing array rather than replacing it.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
