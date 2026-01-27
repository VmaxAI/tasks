# Bug Report

### Describe the bug
When parsing HTML templates with opening tags, the tag name callbacks are receiving incorrect position information. The `onopentagname` callback is being called with `-1` as the start position instead of the actual section start position where the tag name begins.

### Reproduction
```js
const parser = new Tokenizer({
  onopentagname(start, end) {
    console.log('Tag name start:', start, 'end:', end)
    // Expected: start should be a valid position (e.g., 1)
    // Actual: start is -1
  }
})

parser.parse('<div>')
```

### Expected behavior
The `onopentagname` callback should receive the correct start position of the tag name in the input string, not `-1`. This is needed for accurate source mapping and error reporting.

### Additional context
This affects any tooling that relies on accurate position information from the tokenizer, such as:
- Source maps generation
- Error highlighting in IDEs
- Template debugging tools

The tag name end position appears to be correct, but the start position is always `-1` which makes it impossible to accurately locate tag names in the source.

---
Repository: /testbed
