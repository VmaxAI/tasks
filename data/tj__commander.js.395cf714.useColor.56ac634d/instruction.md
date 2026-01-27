# Bug Report

### Describe the bug

The `FORCE_COLOR` environment variable is not being respected correctly. When I set `FORCE_COLOR=0` to explicitly disable colors, the output still shows colors. Similarly, the `CLICOLOR_FORCE` variable seems to have inverted logic.

### Reproduction

```js
// Set FORCE_COLOR to 0 to disable colors
process.env.FORCE_COLOR = '0';

// Create a command and run it
const program = new Command();
program
  .name('test')
  .description('test command');

// The output still shows colors even though FORCE_COLOR=0
```

Also noticed that when `CLICOLOR_FORCE` is NOT set (undefined), colors are being forced on, which seems backwards.

### Expected behavior

- When `FORCE_COLOR=0` is set, colors should be disabled
- When `CLICOLOR_FORCE` is undefined, it should not force colors on
- The environment variable checks should follow standard conventions used by other CLI tools

### System Info
- Node version: 18.x
- OS: macOS

---
Repository: /testbed
