# Bug Report

### Describe the bug

I'm having an issue with the `.default()` method on options. When I try to set a default value of `0`, `false`, or an empty string `""`, the default value doesn't get set properly. It seems like these falsy values are being ignored.

### Reproduction

```js
const option = new Option('-p, --port <number>', 'port number');
option.default(0, 'default port');

// The defaultValue is not set to 0
console.log(option.defaultValue); // Expected: 0, Actual: undefined
```

Same issue with boolean false:
```js
const option = new Option('--verbose', 'verbose output');
option.default(false);

// The defaultValue is not set to false
console.log(option.defaultValue); // Expected: false, Actual: undefined
```

### Expected behavior

The `.default()` method should accept any value including falsy values like `0`, `false`, and `""`. These are valid default values and should be stored properly.

### Additional context

This seems to have started recently. Previously I could set `0` as a default value for numeric options without any issues.

---
Repository: /testbed
