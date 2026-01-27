# Bug Report

### Describe the bug

The `styleArgumentDescription` method is not applying text styling to argument descriptions. Even when custom styling is configured, the argument descriptions appear unstyled in the help output.

### Reproduction

```js
const { Help } = require('./lib/help');

class CustomHelp extends Help {
  styleDescriptionText(str) {
    return `[STYLED] ${str}`;
  }
}

const help = new CustomHelp();
const result = help.styleArgumentDescription('This is an argument description');

console.log(result);
// Expected: "[STYLED] This is an argument description"
// Actual: "This is an argument description"
```

### Expected behavior

When `styleArgumentDescription` is called, it should return the styled text just like `styleSubcommandDescription` does. If a custom `styleDescriptionText` method is provided, the styling should be applied to argument descriptions.

### Additional context

This seems to affect only argument descriptions. Subcommand descriptions are styled correctly. The issue appears when trying to customize help output formatting.

---
Repository: /testbed
