# Bug Report

### Describe the bug

The usage string styling is not working correctly when `[command]` appears in the usage text. The styling appears to be applied inconsistently depending on the position of `[command]` in the string.

### Reproduction

```js
const help = new Help();
const usageString = 'myapp [options] [command] <file>';
const styled = help.styleUsage(usageString);

// The [command] token doesn't get styled with styleSubcommandText
// Instead it gets styled with styleArgumentText
```

### Expected behavior

When the usage string contains `[command]`, it should be styled using `styleSubcommandText()` regardless of where it appears in the string. Currently it seems like the styling logic checks for bracket/angle bracket patterns before checking for the `[command]` keyword specifically, causing `[command]` to be incorrectly styled as an argument instead of a subcommand.

### System Info
- Node version: 18.x
- Library version: latest

---
Repository: /testbed
