# Bug Report

### Describe the bug
I'm experiencing an issue with the `choices()` method where it seems to be rejecting valid choices and possibly not including all the expected options. When I set up choices for a command option, the validation behavior is completely backwards - it's throwing errors for values that should be allowed.

### Reproduction
```js
const { Option } = require('commander');

const option = new Option('-c, --color <type>', 'choose color')
  .choices(['red', 'green', 'blue']);

// This should work but throws an error
option.parseArg('red');  // InvalidArgumentError: Allowed choices are green,blue.

// Also noticed that 'red' is missing from the error message
```

### Expected behavior
- Valid choices should be accepted without throwing an error
- All specified choices should be available and validated correctly
- The error message should list all the choices that were originally provided

### System Info
- commander.js version: latest
- Node.js version: 18.x

This is blocking my CLI application from working properly. Any help would be appreciated!

---
Repository: /testbed
