# Bug Report

### Describe the bug

I'm having an issue with `requiredOption()` - it's not actually requiring the option to be provided. When I define a required option using this method, the program runs successfully even when the option is not supplied on the command line, which shouldn't be allowed.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .requiredOption('-p, --port <number>', 'port number')
  .parse(process.argv);

console.log('Port:', program.opts().port);
```

Running this without the `-p` flag:
```bash
node app.js
```

Expected: Should throw an error about missing required option
Actual: Program runs without error, port is undefined

### Expected behavior

When using `requiredOption()`, the program should exit with an error if the option is not provided by the user. The whole point of marking an option as required is to enforce that it must be present.

### System Info
- commander version: latest
- Node.js: v18.x

---
Repository: /testbed
