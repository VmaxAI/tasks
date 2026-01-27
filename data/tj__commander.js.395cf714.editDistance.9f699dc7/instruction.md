# Bug Report

### Describe the bug

The `suggestSimilar` function is producing incorrect edit distance calculations for certain string pairs. When comparing strings that differ by transpositions, the calculated distance seems to be off.

### Reproduction

```js
const suggestSimilar = require('./lib/suggestSimilar');

// Example 1: Simple transposition
const word1 = 'ab';
const word2 = 'ba';
const distance = editDistance(word1, word2);
// Expected: 1 (one transposition)
// Getting incorrect result

// Example 2: Longer strings with transpositions
const str1 = 'hello';
const str2 = 'hlelo';
// The edit distance calculation appears incorrect
```

### Expected behavior

The edit distance algorithm should correctly calculate the minimum number of operations (insertions, deletions, substitutions, and transpositions) needed to transform one string into another. For transposed characters, it should count as a single operation.

### Additional context

This appears to affect the suggestion feature when looking for similar command names or options. The suggestions being returned don't always make sense based on what was typed.

---
Repository: /testbed
