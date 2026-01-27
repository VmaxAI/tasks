# Bug Report

### Describe the bug

I'm having an issue with `enablePositionalOptions()` - it seems to be doing the opposite of what it should. When I call `enablePositionalOptions(true)`, positional options are actually disabled, and when I call it with `false`, they get enabled.

Also, the method doesn't return the command instance for chaining when called with `true`, which breaks my code that relies on method chaining.

### Reproduction

```js
const program = new Command();

// This should enable positional options but doesn't
program
  .enablePositionalOptions(true)
  .option('-p, --port <number>', 'port number');  // TypeError: Cannot read property 'option' of undefined

// And this enables them when it shouldn't
program.enablePositionalOptions(false);
// positional options are now enabled instead of disabled
```

### Expected behavior

- `enablePositionalOptions(true)` should enable positional options and return the command for chaining
- `enablePositionalOptions(false)` should disable positional options and return the command for chaining
- The method should always return `this` to support fluent API usage

### System Info
- Node version: v18.x
- commander.js version: latest

This is breaking my CLI tool's configuration. Any help would be appreciated!

---
Repository: /testbed
