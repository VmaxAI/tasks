# Bug Report

### Describe the bug

I'm experiencing unexpected behavior with `createCommand()` when creating multiple commands with the same name but different casing. The method now appears to be normalizing command names to lowercase and caching them, which causes issues when you need case-sensitive command names.

### Reproduction

```js
const program = new Command();

// Create two commands with different casing
const cmdUpperCase = program.createCommand('MyCommand');
const cmdLowerCase = program.createCommand('mycommand');

// Both return the same command instance
console.log(cmdUpperCase === cmdLowerCase); // true (unexpected!)

// Also, the name gets normalized to lowercase
console.log(cmdUpperCase.name()); // 'mycommand' instead of 'MyCommand'
```

Additionally, if you try to create a command with extra whitespace, it gets trimmed and normalized:

```js
const cmd1 = program.createCommand('  TestCmd  ');
const cmd2 = program.createCommand('testcmd');

console.log(cmd1 === cmd2); // true (both normalized to 'testcmd')
```

### Expected behavior

Each call to `createCommand()` should return a new, independent Command instance with the exact name provided (preserving case and whitespace). Command names should be case-sensitive by default, as they were in previous versions.

### System Info
- Node version: 18.x
- OS: macOS

This seems like a recent change that breaks backward compatibility with existing code that relies on case-sensitive command names.

---
Repository: /testbed
