# Bug Report

### Describe the bug

I'm experiencing an issue with help text generation where grouped items are not displaying correctly. When commands or options are organized into groups, some items seem to be missing from the output or the grouping behavior is inconsistent.

### Reproduction

```js
const help = new Help();
const commands = [
  { name: 'cmd1', group: 'basic' },
  { name: 'cmd2', group: 'basic' },
  { name: 'cmd3', group: 'advanced' }
];

const visibleCommands = [
  { name: 'cmd2', group: 'basic' },
  { name: 'cmd3', group: 'advanced' }
];

const grouped = help.groupItems(commands, visibleCommands, (item) => item.group);

// Expected: 'basic' group should contain cmd2, 'advanced' group should contain cmd3
// Actual: Items are not appearing in the correct groups or are missing
```

### Expected behavior

When grouping items for help display, all visible items should appear in their respective groups. The groups should be created in the order they first appear in the unsorted items list, and visible items should be added to those groups in the order they appear in the visible items list.

### System Info
- Node version: 18.x
- Package version: latest

---
Repository: /testbed
