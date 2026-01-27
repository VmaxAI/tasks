# Bug Report

### Describe the bug

When calling `configureOutput()` multiple times, the configuration settings from earlier calls are being overridden instead of being preserved. It seems like the merge order is backwards - new configuration should extend the existing configuration, not replace it.

### Reproduction

```js
const program = new Command();

// Set initial output configuration
program.configureOutput({
  writeOut: (str) => console.log('Custom out:', str),
  writeErr: (str) => console.error('Custom err:', str)
});

// Try to add another configuration option
program.configureOutput({
  outputError: (str, write) => write(`Error: ${str}`)
});

// The writeOut and writeErr from the first call are now lost
// Only outputError remains in the configuration
```

### Expected behavior

Each call to `configureOutput()` should merge with the existing configuration, preserving previously set options. If I configure `writeOut` first and then configure `outputError` separately, both should be present in the final configuration.

### System Info
- commander.js version: latest
- Node version: 18.x

---
Repository: /testbed
