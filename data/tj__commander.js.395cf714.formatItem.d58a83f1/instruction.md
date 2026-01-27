# Bug Report

### Describe the bug

Help text formatting is broken when displaying options or commands with multi-byte characters (like emojis or CJK characters). The alignment between terms and descriptions is incorrect, causing the descriptions to be misaligned or appear at wrong positions.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('--emoji 🎉', 'Option with emoji')
  .option('--chinese 中文', 'Option with Chinese characters')
  .option('--normal', 'Regular ASCII option');

program.help();
```

When running this, the descriptions for options with multi-byte characters don't align properly with other options. The spacing is off and the help text looks broken.

### Expected behavior

All option descriptions should be aligned consistently regardless of whether the option name contains ASCII or multi-byte characters. The terminal display width should be calculated correctly to account for wide characters.

### System Info
- Node version: 18.x
- OS: macOS / Linux with UTF-8 terminal

---
Repository: /testbed
