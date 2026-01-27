# Bug Report

### Describe the bug

I'm having an issue with `requiredOption()` - it's not actually requiring the option to be provided. When I define a required option and run my CLI command without providing it, the program doesn't throw an error or exit. It just continues execution as if the option was optional.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .requiredOption('-p, --port <number>', 'port number')
  .parse(process.argv);

console.log('Port:', program.opts().port);
```

Run without providing the required option:
```bash
node app.js
```

### Expected behavior

The program should throw an error indicating that the required option `-p, --port` is missing. Instead, it runs without any errors and `program.opts().port` is undefined.

### System Info
- commander version: latest
- Node.js: v18.x

---
Repository: /testbed
