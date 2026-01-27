# Bug Report

### Describe the bug

I'm experiencing an issue with regex-based option parsing where the captured value is not being returned correctly. When using a RegExp to parse command-line option values, the parser seems to be returning the wrong capture group.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-p, --port <port>', 'port number', /^(\d+)$/)
  .parse(['node', 'test', '--port', '3000']);

console.log(program.opts().port);
// Expected: '3000'
// Actual: undefined (or default value if set)
```

When the regex has capture groups, the matched value isn't extracted properly. It seems like the wrong group index is being used.

### Expected behavior

When a RegExp is used for option parsing with capture groups, the first captured group should be returned as the parsed value. If the regex matches but the capture group is empty/undefined, it should fall back to the default value.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
