# Bug Report

### Describe the bug

When displaying help text for command arguments that have both choices and a default value, the extra information (choices and default) is not being shown. Only arguments with either choices OR a default value (but not both) display the extra info in parentheses.

### Reproduction

```js
const argument = {
  description: 'Select an option',
  argChoices: ['option1', 'option2', 'option3'],
  defaultValue: 'option1'
};

// Expected output: "Select an option (choices: "option1", "option2", "option3", default: "option1")"
// Actual output: "Select an option"
```

The issue also affects arguments that have choices and default but no description - in that case nothing is displayed at all instead of showing the choices and default in parentheses.

### Expected behavior

When an argument has multiple pieces of extra information (like both choices and a default value), all of that information should be displayed in the help text. The format should be:
- If there's a description: `description (choices: ..., default: ...)`
- If there's no description: `(choices: ..., default: ...)`

### System Info
- Node version: 18.x
- Library version: latest

---
Repository: /testbed
