# Bug Report

### Describe the bug

The usage string styling is not working correctly when there are multiple `[options]` placeholders in the usage text. It seems like only exact matches for `[options]` are being styled, but when the word contains `[options]` as part of a longer string (like `[options...]`), it's not being styled properly.

### Reproduction

```js
const help = new Help();
const usageStr = 'mycommand [options...] <file>';
const styled = help.styleUsage(usageStr);

// Expected: [options...] should be styled as option text
// Actual: [options...] is being styled as argument text instead
```

### Expected behavior

When the usage string contains variations of `[options]` like `[options...]`, it should still be styled using `styleOptionText()` rather than falling through to `styleArgumentText()`. The same logic should apply - if a word contains the `[options]` pattern, it should be treated as an options placeholder regardless of any additional characters.

### System Info
- Node version: 18.x
- OS: macOS

---
Repository: /testbed
