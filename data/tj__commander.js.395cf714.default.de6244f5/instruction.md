# Bug Report

### Describe the bug

When setting a default value with a custom description for command-line options, the description is not being stored correctly. Instead, the actual default value is being used as both the value and the description.

### Reproduction

```js
const { Option } = require('commander');

const option = new Option('-p, --port <number>', 'port number')
  .default(3000, 'default port');

console.log('Default value:', option.defaultValue);  // Expected: 3000
console.log('Default description:', option.defaultValueDescription);  // Expected: 'default port'
```

### Expected behavior

When calling `.default(value, description)`, the `defaultValueDescription` should be set to the provided description string (e.g., 'default port'), not the value itself (3000).

### Actual behavior

The `defaultValueDescription` property contains the same value as `defaultValue` instead of the description string that was passed in.

This affects help text generation where custom descriptions for default values should be displayed but instead show the raw value again.

---
Repository: /testbed
