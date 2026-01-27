# Bug Report

### Describe the bug

I'm encountering an issue with dual options (positive/negative option pairs) where the negative option isn't being stored correctly when both options are defined. It seems like the negative option is getting the wrong value assigned to it.

### Reproduction

```js
const { Option } = require('./lib/option');
const { DualOptions } = require('./lib/option');

// Create a positive option
const positiveOpt = new Option('-f, --force', 'force operation');

// Create a negative option with the same attribute name
const negativeOpt = new Option('--no-force', 'disable force operation');
negativeOpt.negate = true;

// Initialize DualOptions with both
const dualOpts = new DualOptions([positiveOpt, negativeOpt]);

// Check what's stored in negativeOptions
console.log(dualOpts.negativeOptions.get('force'));
// Expected: negativeOpt
// Actual: positiveOpt (the negative option has the positive option's value)
```

### Expected behavior

When both a positive and negative option are defined for the same attribute, the `negativeOptions` map should store the actual negative option, not the positive one. Each option should maintain its own identity and configuration.

### System Info
- Node version: 18.x
- Package version: latest

---
Repository: /testbed
