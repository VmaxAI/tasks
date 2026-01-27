# Bug Report

### Describe the bug

I'm experiencing an issue with text width calculation in the help formatter. When displaying help text that contains certain Unicode characters (specifically characters in the Hangul Jamo range U+1100 to U+11FF), the column alignment appears incorrect. The text seems to be misaligned compared to other rows.

### Reproduction

```js
const help = new Help();

// Text with Hangul Jamo characters
const text1 = 'ᄀᄁᄂᄃ test';
const text2 = 'normal text';

console.log(help.displayWidth(text1)); // Returns incorrect width
console.log(help.displayWidth(text2)); // Returns correct width
```

When these are used in option descriptions or command names, the help output columns don't line up properly. The formatting looks broken because the width calculation doesn't account for these special characters.

### Expected behavior

The `displayWidth()` method should correctly calculate the display width of strings containing Hangul Jamo characters, so that help text columns align properly regardless of the character types used.

### System Info
- Node version: 18.x
- OS: macOS

---
Repository: /testbed
