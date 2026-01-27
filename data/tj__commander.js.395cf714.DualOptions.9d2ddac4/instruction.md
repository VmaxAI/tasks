# Bug Report

### Describe the bug

I'm experiencing an issue with option negation when using dual options. The `valueFromOption` method seems to be returning incorrect results, causing options with negation to not work as expected.

When I define a dual option (like `--foo` / `--no-foo`) and try to determine which variant was used based on the value, the logic appears to be inverted. This is causing my CLI to misidentify which option the user actually specified.

### Reproduction

```js
const { DualOptions } = require('./lib/option');

// Set up dual options
const dualOpts = new DualOptions();
dualOpts.addDualOption('--foo', '--no-foo');

// Create option objects
const fooOption = { 
  attributeName: () => 'foo',
  negate: false 
};
const noFooOption = { 
  attributeName: () => 'foo',
  negate: true 
};

// These return unexpected results
console.log(dualOpts.valueFromOption(true, fooOption));   // Expected: true, but getting false
console.log(dualOpts.valueFromOption(false, noFooOption)); // Expected: true, but getting false
```

### Expected behavior

When calling `valueFromOption(value, option)`, it should correctly identify whether the given value came from the specified option variant. For example:
- `valueFromOption(true, fooOption)` should return `true` (the value `true` came from `--foo`)
- `valueFromOption(false, noFooOption)` should return `true` (the value `false` came from `--no-foo`)

Instead, the method seems to be returning inverted results, making it impossible to determine which option variant was actually used.

### System Info
- Node version: v18.x
- Package version: latest

---
Repository: /testbed
