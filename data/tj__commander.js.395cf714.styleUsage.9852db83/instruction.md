# Bug Report

### Describe the bug

When displaying command usage strings in help text, the spacing between words is being removed. The usage line appears as one continuous string without any spaces separating the command parts.

### Reproduction

```js
const help = new Help();
const usageString = 'mycommand [options] <input> [output]';
const styled = help.styleUsage(usageString);
console.log(styled);
// Output: 'mycommand[options]<input>[output]'
// Expected: 'mycommand [options] <input> [output]'
```

After styling the usage string, all the spaces between the different parts (command name, options, arguments) are gone, making the help text difficult to read.

### Expected behavior

The usage string should maintain proper spacing between each component. For example:
```
mycommand [options] <input> [output]
```

Instead of:
```
mycommand[options]<input>[output]
```

### System Info
- Node version: 18.x
- OS: Linux

---
Repository: /testbed
