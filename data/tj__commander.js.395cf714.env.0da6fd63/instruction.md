# Bug Report

### Describe the bug

When calling `.env()` multiple times on the same option, the environment variable names are being concatenated together instead of being replaced. This causes the option to look for an environment variable with a concatenated name that doesn't exist.

### Reproduction

```js
const { Option } = require('commander');

const option = new Option('-p, --port <number>', 'port number');
option.env('PORT');
option.env('SERVER_PORT'); // Should replace 'PORT' with 'SERVER_PORT'

// The option now looks for 'PORTSERVER_PORT' instead of 'SERVER_PORT'
```

### Expected behavior

Each call to `.env()` should replace the previous environment variable name, not concatenate to it. The second call should set the env var to `'SERVER_PORT'`, not `'PORTSERVER_PORT'`.

### System Info
- commander version: latest
- Node version: 18.x

---
Repository: /testbed
