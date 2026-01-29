# Bug Report

### Describe the bug
When using `stringEncaseCRLFWithFirstIndex()` function, the first character after each line break is being skipped/missing in the output. The function seems to be dropping characters when processing strings with newlines.

### Reproduction
```js
import {stringEncaseCRLFWithFirstIndex} from './utilities.js';

const input = 'hello\nworld\ntest';
const result = stringEncaseCRLFWithFirstIndex(input, '[', ']', input.indexOf('\n'));

console.log(result);
// Output: 'hello[\n]orld[n]est'
// Expected: 'hello[\n]world[\n]test'
```

The character immediately following each newline is being lost. In the example above, 'w' from "world" and 't' from "test" are missing.

### Expected behavior
All characters should be preserved in the output string, with only the specified prefix and postfix added around line breaks.

### Additional context
This appears to affect any string with multiple line breaks where the function is called with an index pointing to a newline character. The issue is consistent across different input strings.

---
Repository: /testbed
