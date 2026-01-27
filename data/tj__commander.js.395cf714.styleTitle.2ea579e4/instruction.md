# Bug Report

### Describe the bug

The `styleTitle()` method is truncating the last character of title strings. When formatting help text titles, the final character is being dropped from the output.

### Reproduction

```js
const help = new Help();

// Last character is missing
console.log(help.styleTitle('Command')); 
// Expected: "Command" (or styled version)
// Actual: "Comman"

console.log(help.styleTitle('Usage Information'));
// Expected: "Usage Information" (or styled version)  
// Actual: "Usage Informatio"
```

### Expected behavior

The `styleTitle()` method should return the complete title string with all characters intact. No characters should be removed from the input.

### Additional context

This appears to affect any non-empty string passed to the method. Single character strings would result in empty output, and multi-character strings lose their last character.

---
Repository: /testbed
