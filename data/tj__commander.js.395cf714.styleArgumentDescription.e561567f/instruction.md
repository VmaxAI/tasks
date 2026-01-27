# Bug Report

### Describe the bug

I'm experiencing an issue with argument descriptions in the help output. When I define argument descriptions in my CLI, they're not being displayed correctly. The descriptions seem to disappear or not show up at all in the help text.

### Reproduction

```js
const program = require('commander');

program
  .argument('<file>', 'Input file to process')
  .argument('[output]', 'Output destination')
  .parse();

program.help();
```

When running this, the argument descriptions don't appear in the help output as expected.

### Expected behavior

The argument descriptions should be visible in the help text, showing "Input file to process" and "Output destination" next to their respective arguments.

### System Info
- Node version: 18.x
- Commander version: latest

Has anyone else run into this? It was working fine before but now the descriptions just aren't showing up.

---
Repository: /testbed
