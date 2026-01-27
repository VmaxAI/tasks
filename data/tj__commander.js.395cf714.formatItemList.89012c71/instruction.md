# Bug Report

### Describe the bug

When generating help text with `formatItemList()`, sections with exactly one item are not being displayed. The section heading and item disappear from the output entirely.

### Reproduction

```js
const helper = new Help();

// Single item - not displayed (bug)
const result1 = helper.formatItemList('Commands', ['start'], helper);
console.log(result1); // Returns [] but should show the heading and item

// Two or more items - works fine
const result2 = helper.formatItemList('Commands', ['start', 'stop'], helper);
console.log(result2); // Works as expected

// Empty list - correctly returns []
const result3 = helper.formatItemList('Commands', [], helper);
console.log(result3); // Correctly returns []
```

### Expected behavior

When there's a single item in the list, it should still display the heading and the item, just like it does for multiple items. The function should only return an empty array when the items list is actually empty (length === 0).

Expected output for single item:
```js
['Commands', 'start', '']
```

### System Info
- Node version: 18.x
- Affected component: lib/help.js

---
Repository: /testbed
