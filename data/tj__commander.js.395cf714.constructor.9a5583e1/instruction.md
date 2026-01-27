# Bug Report

### Describe the bug

When using dual options (positive and negative flags), the options are being assigned to the wrong maps. Negative options are being stored as positive options and vice versa, which causes the dual option detection logic to fail completely.

### Reproduction

```js
const { Option } = require('commander');

// Create a positive option (no negate flag)
const positiveOption = new Option('--color', 'enable color');

// Create a negative option (with negate flag)
const negativeOption = new Option('--no-color', 'disable color');
negativeOption.negate = true;

const dualOptions = new DualOptions([positiveOption, negativeOption]);

// The options are stored in the wrong maps
console.log(dualOptions.positiveOptions.has('color')); // Expected: true, Actual: false
console.log(dualOptions.negativeOptions.has('color')); // Expected: true, Actual: false
console.log(dualOptions.dualOptions.has('color')); // Expected: true, Actual: false
```

### Expected behavior

- Positive options (without negate flag) should be stored in `positiveOptions`
- Negative options (with negate flag) should be stored in `negativeOptions`  
- When both exist for the same attribute name, it should be added to `dualOptions`

### Current behavior

The options are being stored in reversed maps - positive options go to negative map and negative options go to positive map. This breaks the entire dual option mechanism.

---
Repository: /testbed
