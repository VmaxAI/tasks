# Bug Report

### Describe the bug

I'm experiencing an issue with the DualOptions class where positive and negative options appear to be swapped. When I create options with `negate: true`, they're being treated as positive options, and vice versa.

### Reproduction

```js
const options = [
  { negate: false, attributeName: () => 'verbose' },
  { negate: true, attributeName: () => 'verbose' }
];

const dualOptions = new DualOptions(options);

// Expected: positiveOptions should contain the non-negated option
// Actual: negativeOptions contains it instead

console.log(dualOptions.positiveOptions.has('verbose')); // false (should be true)
console.log(dualOptions.negativeOptions.has('verbose')); // true (should be false)
```

### Expected behavior

Options with `negate: false` should be stored in `positiveOptions`, and options with `negate: true` should be stored in `negativeOptions`. The dual options detection should work correctly based on this mapping.

### Additional context

This is causing issues in my CLI application where negated flags (like `--no-color`) are being processed incorrectly. The behavior seems inverted from what the property names suggest.

---
Repository: /testbed
