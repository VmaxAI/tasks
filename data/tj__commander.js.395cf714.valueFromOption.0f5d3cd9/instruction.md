# Bug Report

### Describe the bug

I'm experiencing an issue with dual options where the `valueFromOption` method is returning incorrect boolean values. The logic seems inverted - it's returning `true` when it should return `false` and vice versa.

### Reproduction

```js
const dualOptions = new DualOptions();
// Set up a dual option with negation
const option = {
  attributeName: () => 'verbose',
  negate: false
};

// Register the option
dualOptions.addDualOption(option);

// Check if value came from option
const result = dualOptions.valueFromOption(true, option);
// Returns true but should return false based on the option configuration
```

### Expected behavior

The method should correctly determine whether a value originated from a specific option by checking the negation state and preset arguments. Currently it appears to be doing the opposite of what's expected.

### Additional context

This is affecting command-line argument parsing where dual options (like `--verbose` / `--no-verbose`) need to determine which form was used. The inverted logic is causing the wrong option to be identified as the source of the value.

---
Repository: /testbed
