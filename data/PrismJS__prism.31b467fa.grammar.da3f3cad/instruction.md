# Bug Report

### Describe the bug
The Pure language syntax highlighting appears to be broken. The grammar definition seems to have incorrect indentation which is causing the entire language support to fail. Code written in Pure is not being highlighted properly in my editor.

### Reproduction
1. Create a file with `.pure` extension
2. Add any Pure language code, for example:
```pure
// Simple Pure function
factorial n = if n <= 0 then 1 else n * factorial (n-1);
```
3. The syntax highlighting doesn't work at all

### Expected behavior
Pure language code should be properly syntax highlighted with keywords, comments, strings, and other language constructs being colored according to the grammar rules.

### System Info
- Using the latest version from main branch
- This seems to have started recently, possibly after a recent update to the Pure language definition

---
Repository: /testbed
