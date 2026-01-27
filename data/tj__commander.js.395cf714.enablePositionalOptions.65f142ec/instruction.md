# Bug Report

### Describe the bug

I'm having an issue with `enablePositionalOptions()` where calling it seems to break method chaining in certain scenarios. After calling this method, subsequent chained method calls fail because the method doesn't return the command instance properly.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// This breaks - enablePositionalOptions doesn't return the command
program
  .enablePositionalOptions(false)
  .option('-d, --debug', 'enable debugging');  // Error: Cannot read property 'option' of undefined
```

When I call `enablePositionalOptions(false)`, it seems like the method doesn't return `this` anymore, which breaks the fluent API pattern that Commander.js uses throughout.

### Expected behavior

The method should always return the command instance to allow method chaining, regardless of the parameter value passed to it. This is consistent with how other configuration methods in Commander work.

```js
// Should work like this
program
  .enablePositionalOptions(false)
  .option('-d, --debug', 'enable debugging')
  .action(() => {
    // ...
  });
```

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
