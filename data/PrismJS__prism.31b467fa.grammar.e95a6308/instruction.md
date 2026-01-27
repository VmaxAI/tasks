# Bug Report

### Describe the bug
I'm experiencing an issue with CSV parsing where quoted values are not being recognized correctly. When a CSV contains quoted strings, the tokenization seems to break and the quotes are not properly handled.

### Reproduction
```csv
name,age,city
"John Doe",30,"New York"
"Jane Smith",25,"Los Angeles"
```

When parsing this CSV, the quoted values like `"John Doe"` and `"New York"` are not being tokenized as complete values. It appears that the closing quote is being incorrectly matched or the pattern is not recognizing the end of quoted strings properly.

### Expected behavior
Quoted CSV values should be treated as single tokens, with the entire quoted string (including internal quotes if escaped) being recognized as one value. For example, `"John Doe"` should be a single value token, not split up.

### Additional context
This seems to affect any CSV file with quoted fields. The issue is particularly noticeable when:
- Values contain spaces
- Values contain commas within quotes
- Multiple quoted fields are on the same line

The tokenizer appears to be stopping at the wrong position when processing quoted strings.

---
Repository: /testbed
