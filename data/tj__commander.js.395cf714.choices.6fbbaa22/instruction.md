# Bug Report

### Describe the bug

I'm experiencing an issue with the `choices()` method on arguments. When I define an argument with choices and try to pass multiple values (variadic argument), the behavior seems inverted - it's treating non-variadic arguments as variadic and vice versa.

### Reproduction

```js
const program = new Command();

// Non-variadic argument with choices
program
  .argument('<color>', 'color choice')
  .choices(['red', 'green', 'blue']);

// When I pass a single value, it seems to be concatenating/treating it as variadic
// Expected: just return the single value
// Actual: attempts to concatenate as if it were variadic

// Similarly, for variadic arguments with choices:
program
  .argument('<colors...>', 'color choices')
  .choices(['red', 'green', 'blue']);

// When passing multiple values, it's not concatenating them properly
// Expected: should concatenate all values
// Actual: just returns the last value
```

### Expected behavior

- Non-variadic arguments with choices should return the single value as-is
- Variadic arguments with choices should concatenate all provided values into an array

### Additional context

This seems like the logic for handling variadic vs non-variadic arguments got flipped somehow. The concatenation behavior is happening when it shouldn't, and not happening when it should.

---
Repository: /testbed
