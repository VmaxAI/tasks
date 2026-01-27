# Bug Report

### Describe the bug

I'm having an issue with the `makeOptionMandatory()` method - it seems to be setting the mandatory flag to the opposite of what I expect. When I pass `true`, the option is not treated as mandatory, and when I pass `false`, it becomes mandatory instead.

### Reproduction

```js
const option = new Option('-f, --file <path>');

// This should make the option mandatory, but it doesn't work
option.makeOptionMandatory(true);
console.log(option.mandatory); // Expected: true, but getting false

// This should make it optional, but it becomes mandatory
option.makeOptionMandatory(false);
console.log(option.mandatory); // Expected: false, but getting true
```

### Expected behavior

When calling `makeOptionMandatory(true)`, the option should be mandatory. When calling `makeOptionMandatory(false)`, the option should be optional. The behavior seems to be inverted.

### Additional context

This is breaking my CLI application where I need to conditionally make certain options mandatory based on other flags. The logic appears to be backwards from what the method name and parameter suggest.

---
Repository: /testbed
