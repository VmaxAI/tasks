# Bug Report

### Describe the bug

The `executableDir()` method is not working as expected. When I try to set a custom executable directory, it returns the current directory instead of setting the new one. Conversely, when I try to get the current executable directory without passing any arguments, it sets the directory to `undefined`.

### Reproduction

```js
const program = new Command();

// Try to set executable directory
program.executableDir('/custom/path');

// The directory is not set, returns undefined instead
console.log(program.executableDir()); // Expected: '/custom/path', Actual: undefined

// Try to get executable directory without setting
const cmd = new Command();
const dir = cmd.executableDir();
// This actually sets the directory to undefined instead of returning it
```

### Expected behavior

- When calling `executableDir(path)` with a path argument, it should set the executable directory and return the command instance for chaining
- When calling `executableDir()` without arguments, it should return the current executable directory value

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
