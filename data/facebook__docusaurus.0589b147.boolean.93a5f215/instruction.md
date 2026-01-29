# Bug Report

### Describe the bug

The `duplicates()` utility function is returning incorrect results. When I pass an array with duplicate values, it's not detecting them properly and returns an empty array instead of the actual duplicates.

### Reproduction

```js
import { duplicates } from '@docusaurus/theme-common/lib/utils/jsUtils';

const arr = [1, 2, 3, 2, 4, 3];
const result = duplicates(arr);

console.log(result); // Expected: [2, 3], Actual: []
```

The function seems to be failing to identify duplicate elements in arrays. I've tried with both primitive values and objects, and it's not working as expected in either case.

### Expected behavior

The `duplicates()` function should return an array containing the duplicate values found in the input array. For the example above, it should return `[2, 3]` since those values appear more than once.

### System Info

- @docusaurus/theme-common version: latest
- Node version: 18.x

---
Repository: /testbed
