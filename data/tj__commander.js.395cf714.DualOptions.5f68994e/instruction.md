# Bug Report

### Describe the bug

I'm experiencing an issue with dual options (options that have both positive and negative forms, like `--foo` and `--no-foo`). When I set a dual option, the value doesn't seem to be stored or retrieved correctly - it appears to be using the wrong option configuration internally.

### Reproduction

```js
const program = new Command();

program
  .option('--foo', 'enable foo')
  .option('--no-foo', 'disable foo');

program.parse(['node', 'test', '--foo']);

// Expected: true
// Actual: behaves as if --no-foo was passed
console.log(program.opts().foo);
```

Similarly, when using the negative form:

```js
program.parse(['node', 'test', '--no-foo']);

// Expected: false  
// Actual: behaves as if --foo was passed
console.log(program.opts().foo);
```

### Expected behavior

When `--foo` is passed, `opts().foo` should be `true`. When `--no-foo` is passed, `opts().foo` should be `false`. The positive and negative forms of dual options should work correctly and return the appropriate values.

### Additional context

This seems to affect all dual options, not just boolean flags. The behavior is inverted from what I would expect - it's as if the positive and negative options are swapped internally.

---
Repository: /testbed
