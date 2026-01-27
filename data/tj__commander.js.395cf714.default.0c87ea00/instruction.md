# Bug Report

### Describe the bug

The `default()` method on Argument is not working correctly. When I set a default value with a description, the method doesn't seem to be chainable anymore and the default value itself gets overwritten.

### Reproduction

```js
const { Argument } = require('commander');

const arg = new Argument('<value>', 'some argument')
  .default('myDefault', 'default description')
  .choices(['a', 'b', 'c']);  // This throws an error about .choices not being a function
```

Also, when I check the defaultValue property after calling `default()`, it contains the description string instead of the actual default value:

```js
const arg = new Argument('<value>', 'some argument');
arg.default('myDefault', 'default description');
console.log(arg.defaultValue);  // Prints 'default description' instead of 'myDefault'
```

### Expected behavior

- The `default()` method should return the Argument instance to allow method chaining
- The `defaultValue` property should contain the actual default value, not the description
- The `defaultValueDescription` property should contain the description

### System Info
- commander version: latest
- Node version: 18.x

---
Repository: /testbed
