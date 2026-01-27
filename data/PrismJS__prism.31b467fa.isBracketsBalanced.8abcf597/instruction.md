# Bug Report

### Describe the bug

I'm experiencing an issue with bracket matching in naniscript syntax. When I have brackets at the beginning of an expression, they're not being validated correctly and the parser is giving incorrect results about whether brackets are balanced.

### Reproduction

```js
// This should be detected as unbalanced but isn't
const test1 = '[unmatched';

// This should be balanced but is reported as unbalanced
const test2 = '[matched]';

// Starting brackets seem to be completely ignored
const test3 = '{something}';
```

It seems like the first character in the input is being skipped during bracket validation. Also, when I have a closing bracket that should match an opening bracket, it's being rejected as unbalanced instead.

### Expected behavior

The bracket validation should:
1. Check all characters in the input including the first one
2. Correctly match opening and closing brackets
3. Return `true` for balanced brackets like `[]` or `{}`
4. Return `false` for unbalanced brackets like `[` or `]`

### System Info
- Language: naniscript
- Version: latest

---
Repository: /testbed
