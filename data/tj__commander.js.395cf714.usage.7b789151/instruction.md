# Bug Report

### Describe the bug

When calling the `usage()` method in a chained manner, the method returns the usage string instead of the Command instance, breaking method chaining.

### Reproduction

```js
const program = new Command();

// This should work but throws an error
program
  .usage('<file>')
  .option('-d, --debug', 'enable debug mode')
  .action(() => {});
```

The chaining breaks because `usage()` returns a string instead of the Command instance when setting a custom usage string.

### Expected behavior

The `usage()` method should return `this` (the Command instance) to allow method chaining, just like other configuration methods like `option()`, `description()`, etc.

```js
// This should work
program
  .usage('<file>')
  .option('-d, --debug', 'enable debug mode');
```

### Additional context

This seems to have started recently. Other methods in the API support chaining, so this feels inconsistent.

---
Repository: /testbed
