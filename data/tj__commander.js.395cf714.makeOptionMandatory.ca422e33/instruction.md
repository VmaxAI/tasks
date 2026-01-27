# Bug Report

### Describe the bug

I'm having an issue with `makeOptionMandatory()` - it seems to be doing the opposite of what it should do. When I call `makeOptionMandatory(true)` on an option, it's not being treated as mandatory, and when I call `makeOptionMandatory(false)`, it becomes mandatory instead.

### Reproduction

```js
const option = new Option('-f, --file <path>', 'input file');

// This should make the option mandatory, but it doesn't work
option.makeOptionMandatory(true);

// The option is not actually mandatory even though it should be
```

Also, the method seems to return something unexpected instead of the option instance itself, so I can't chain other methods after calling it.

### Expected behavior

- `makeOptionMandatory(true)` should make the option mandatory
- `makeOptionMandatory(false)` should make the option optional
- The method should return the option instance for method chaining

### System Info
- Node version: v18.x
- commander.js version: latest

---
Repository: /testbed
