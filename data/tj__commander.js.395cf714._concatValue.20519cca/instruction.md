# Bug Report

### Describe the bug

I'm experiencing an issue with options that have the `concat` variadic processor. When I specify the same option multiple times on the command line, instead of concatenating the values into an array, only the last value is being used.

### Reproduction

```js
program
  .option('-i, --input <file>', 'input file')
  .configureOption('input', { variadic: true, concat: true });

// Running: node app.js -i file1.txt -i file2.txt -i file3.txt
// Expected: { input: ['file1.txt', 'file2.txt', 'file3.txt'] }
// Actual: { input: 'file3.txt' }
```

The first value gets replaced instead of being added to an array. It seems like the concatenation logic isn't working properly when building up the array from multiple option invocations.

### Expected behavior

When using an option with concat enabled multiple times, all values should be collected into an array, not just the last one.

### System Info
- Node version: 18.x
- OS: Linux

---
Repository: /testbed
