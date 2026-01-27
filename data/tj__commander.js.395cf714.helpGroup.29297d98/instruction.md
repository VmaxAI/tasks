# Bug Report

### Describe the bug

The `helpGroup()` method seems to be broken after a recent update. When I call it on an option, it doesn't return the option instance anymore, which breaks method chaining.

### Reproduction

```js
const { Option } = require('commander');

const option = new Option('-f, --foo', 'foo option');

// This used to work but now throws an error
option
  .helpGroup('My Group')
  .default('bar');
```

The error I get is something like "Cannot read property 'default' of undefined" because `helpGroup()` is not returning anything.

### Expected behavior

The `helpGroup()` method should return the Option instance so that methods can be chained together like other option configuration methods.

### Additional context

This is breaking existing code that relies on chaining multiple option configuration methods together. All other methods like `.default()`, `.choices()`, etc. support chaining, so `helpGroup()` should too.

---
Repository: /testbed
