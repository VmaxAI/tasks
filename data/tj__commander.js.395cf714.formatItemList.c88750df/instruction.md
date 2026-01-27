# Bug Report

### Describe the bug
When using `formatItemList()`, the heading is no longer being displayed in the formatted output. The method seems to be skipping the title/heading that should appear before the list of items.

### Reproduction
```js
const helper = new Help();
const items = ['item1', 'item2', 'item3'];
const result = helper.formatItemList('My Heading', items, helper);

// Expected: ['My Heading', 'item1', 'item2', 'item3', '']
// Actual: ['item1', 'item2', 'item3', '']
// The heading is missing!
```

### Expected behavior
The formatted list should include the styled heading as the first element, followed by the items, and then an empty string separator.

### Additional context
This affects any code that relies on `formatItemList()` to display categorized help information with proper headings. The headings are important for organizing and presenting the information to users.

---
Repository: /testbed
