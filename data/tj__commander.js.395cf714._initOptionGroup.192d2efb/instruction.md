# Bug Report

Title: Default option group not being applied to options without explicit group

I've encountered an issue where options are not being assigned to the default option group when they don't have an explicit `helpGroupHeading` set. 

Steps to reproduce:
1. Set a default option group using `_defaultOptionGroup`
2. Add options without specifying a `helpGroupHeading`
3. The options don't appear in the default group as expected

Example:
```js
const program = new Command();
program._defaultOptionGroup = 'Common Options';

program.option('-v, --verbose', 'verbose output');
program.option('-q, --quiet', 'quiet mode');

// Expected: both options should be in 'Common Options' group
// Actual: options are not grouped under the default group
```

### Expected behavior
Options without an explicit help group should automatically be assigned to the default option group when one is configured.

### Current behavior
Options are only grouped if they already have a `helpGroupHeading` set, which defeats the purpose of having a default group.

This seems like it might be a regression - the default grouping mechanism doesn't appear to be working correctly anymore.

---
Repository: /testbed
