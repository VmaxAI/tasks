# Bug Report

Title: optionsGroup() method returns wrong value when setting heading

I've encountered an issue with the `optionsGroup()` method where it's not behaving as expected when getting/setting the default option group heading.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

// Setting a heading should return the command for chaining
const result = program.optionsGroup('My Options');
console.log(result); // Expected: Command instance, Actual: string value

// Getting the heading should return the current heading
const heading = program.optionsGroup();
console.log(heading); // Expected: 'My Options', Actual: empty string or undefined
```

### Expected behavior

- When called WITH an argument, `optionsGroup(heading)` should set the heading and return the Command instance (for method chaining)
- When called WITHOUT an argument, `optionsGroup()` should return the current heading string

### Current behavior

The getter/setter logic appears to be inverted - it returns the heading when trying to set it, and tries to set it when trying to get it.

This breaks method chaining and makes it impossible to retrieve the currently set option group heading.

---
Repository: /testbed
