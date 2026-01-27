# Bug Report

### Describe the bug

I'm experiencing an issue with the help formatting where the first item in a list is being skipped when displaying help output. It seems like items aren't being displayed correctly - the first element is missing from the formatted output.

### Reproduction

```js
const helper = new Help();
const items = ['Option 1', 'Option 2', 'Option 3'];
const result = helper.formatItemList('Available Options:', items, helper);

// Expected output:
// ['Available Options:', 'Option 1', 'Option 2', 'Option 3', '']

// Actual output:
// ['Available Options:', '', 'Option 2', 'Option 3', '']
// Notice 'Option 1' is missing and there's an extra empty string
```

When formatting help items with a heading, the first item in the list doesn't appear in the output. Instead, there's an empty line where it should be.

### Expected behavior

All items should be included in the formatted output in the correct order, with the heading followed by all items and then a trailing empty line for spacing.

### System Info
- Node version: Latest
- Library version: Current main branch

---
Repository: /testbed
