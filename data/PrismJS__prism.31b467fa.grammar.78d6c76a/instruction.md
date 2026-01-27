# Bug Report

### Describe the bug

The PARI/GP language syntax highlighting is broken for keywords. When writing PARI/GP code, keywords like `break`, `for`, `while`, etc. are not being highlighted correctly. It seems like the pattern matching for keywords has become overly permissive and is now matching things it shouldn't.

### Reproduction

```js
// PARI/GP code sample
for(i=1, 10, print(i))
break
while(x < 5, x++)
```

When highlighting the above code, the keywords are not recognized properly. The pattern seems to be treating individual characters with spaces between them incorrectly.

### Expected behavior

Keywords should be highlighted correctly when they appear in normal PARI/GP code. The syntax highlighter should recognize `for`, `break`, `while`, etc. as keywords without requiring spaces between every character.

### Additional context

This appears to have started happening recently. The keyword matching regex seems to have an issue where it's processing the entire joined keyword string character-by-character instead of processing each individual keyword.

---
Repository: /testbed
