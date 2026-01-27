# Bug Report

### Describe the bug

I'm experiencing an issue with command text styling in help output. When using `styleCommandText()`, the last character of the command text is being displayed without the bold styling applied to the rest of the text.

### Reproduction

```js
const help = new Help();
const styledCommand = help.styleCommandText('mycommand');
// Expected: entire 'mycommand' text to be bold
// Actual: 'mycomman' is bold but 'd' is not
```

When displaying help text for commands, the styling appears to split the last character from the rest of the text, causing inconsistent formatting in the terminal output.

### Expected behavior

The entire command text should be styled uniformly with bold formatting. All characters in the command name should have the same ANSI styling applied.

### System Info
- Node version: 18.x
- Terminal: Various (iTerm2, Terminal.app, etc.)

---
Repository: /testbed
