# Bug Report

### Describe the bug

The usage string formatting appears broken - the styling is being applied to the wrong parts of the usage line. Command names and arguments are getting swapped styles, and there's extra spacing between words.

### Reproduction

When I generate help text for a command with a usage pattern like:

```
mycli subcommand [options] <required> [optional]
```

The styling gets applied incorrectly. The command/subcommand names are being styled as arguments, and the actual arguments (things in `<>` and `[]` brackets) are being styled as commands.

Also noticed that words in the usage string are being joined with double spaces instead of single spaces, which looks weird in the terminal output.

### Expected behavior

- Command names should be styled with command styling
- Arguments in `<>` or `[]` should be styled with argument styling  
- `[options]` should get option styling
- `[command]` should get subcommand styling
- Words should be separated by single spaces, not double spaces

### System Info
- Node version: v18.x
- OS: macOS

---
Repository: /testbed
