# Bug Report

### Describe the bug

I'm experiencing an issue with option name parsing where long and short option names are being processed incorrectly. It seems like the prefixes are being stripped in the wrong way - long options (with `--`) are having only a single dash removed, and short options (with `-`) are trying to have double dashes removed.

### Reproduction

```js
const { Option } = require('commander');

// Long option case
const longOpt = new Option('--verbose', 'verbose output');
console.log(longOpt.name()); // Expected: 'verbose', but getting '-verbose'

// Short option case  
const shortOpt = new Option('-v', 'verbose output');
console.log(shortOpt.name()); // Expected: 'v', but getting '-v' (or unchanged)
```

### Expected behavior

- Long options (e.g., `--verbose`) should have both dashes stripped and return `verbose`
- Short options (e.g., `-v`) should have the single dash stripped and return `v`

### System Info
- commander version: latest
- Node.js: v18.x

This is causing issues in my application where I need to access option names programmatically. The returned names still contain dashes which breaks my configuration mapping logic.

---
Repository: /testbed
