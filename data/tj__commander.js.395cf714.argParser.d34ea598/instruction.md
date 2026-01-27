# Bug Report

### Describe the bug

I'm experiencing an issue with the `argParser()` method - it's not returning the `Argument` instance anymore, which breaks method chaining. After calling `argParser()`, I can't chain other methods like I used to.

### Reproduction

```js
const { Argument } = require('commander');

const arg = new Argument('<value>', 'description');

// This used to work but now throws an error
arg
  .argParser((value) => parseInt(value))
  .choices([1, 2, 3]);  // TypeError: Cannot read property 'choices' of undefined
```

The issue is that `argParser()` no longer returns `this`, so method chaining is broken. This worked fine in previous versions.

### Expected behavior

`argParser()` should return the `Argument` instance to allow method chaining, just like other builder methods in the API.

```js
// Should be able to chain methods
arg
  .argParser(customParser)
  .choices(['a', 'b', 'c'])
  .default('a');
```

### System Info
- Node version: 16.x
- commander version: latest

---
Repository: /testbed
