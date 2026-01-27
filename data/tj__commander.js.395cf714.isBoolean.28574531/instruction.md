# Bug Report

### Describe the bug

After a recent update, I'm encountering an issue where boolean options are not being recognized correctly. When I define an option without required/optional/negate flags, it should be treated as a boolean option, but instead I'm getting unexpected behavior.

### Reproduction

```js
const { Option } = require('commander');

const option = new Option('-d, --debug', 'enable debug mode');

// This should return true for a boolean option
console.log(option.isBoolean()); // TypeError: option.isBoolean is not a function
```

### Expected behavior

The `isBoolean()` method should be available on Option instances and should return `true` for options that don't have required, optional, or negate flags set.

### Additional context

This appears to have broken in the latest version. The `isBoolean()` method seems to have been removed or replaced with something else. My CLI application relies on this to determine how to parse option values.

---
Repository: /testbed
