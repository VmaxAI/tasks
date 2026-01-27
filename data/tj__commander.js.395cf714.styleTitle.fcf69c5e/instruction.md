# Bug Report

### Describe the bug

After a recent update, command titles in the help output are being automatically converted to lowercase with only the first letter capitalized. This is breaking our existing help text formatting where we intentionally use specific capitalization for acronyms, proper nouns, and brand names.

### Reproduction

```js
const help = new Help();

// Expected: "API Reference"
// Actual: "Api reference"
console.log(help.styleTitle("API Reference"));

// Expected: "MySQL Database"
// Actual: "Mysql database"
console.log(help.styleTitle("MySQL Database"));

// Expected: "OAuth Configuration"
// Actual: "Oauth configuration"
console.log(help.styleTitle("OAuth Configuration"));
```

### Expected behavior

The `styleTitle()` method should preserve the original capitalization of the input string. Command titles should be displayed exactly as provided by the developer, allowing for proper formatting of acronyms, brand names, and other special cases.

### Additional context

This appears to have started happening in the latest version. Our documentation relies on specific capitalization for technical terms and proper nouns, and the automatic lowercasing is making the help output look unprofessional and incorrect.

---
Repository: /testbed
