# Bug Report

### Describe the bug

I'm experiencing an issue with syntax highlighting in Razor/CSHTML files after a recent update. Nested patterns in the code don't seem to be working correctly - specifically, deeply nested parentheses, brackets, and braces are not being highlighted properly.

### Reproduction

Create a CSHTML file with nested expressions like:

```cshtml
@(someFunc(anotherFunc(deeplyNested(value))))
@{
    var result = Calculate(
        GetValue(
            ProcessData(input)
        )
    );
}
```

The syntax highlighting breaks down at the first level of nesting. The outer expressions are highlighted correctly, but anything nested inside loses proper highlighting.

### Expected behavior

All levels of nested expressions should be highlighted correctly, regardless of depth. Previously this was working fine with multiple levels of nesting.

### Additional context

This seems to affect:
- Nested parentheses in function calls
- Nested brackets in array access
- Nested curly braces in code blocks
- Nested angle brackets in generic types

The issue appears to be most noticeable when you have 2 or more levels of nesting.

---
Repository: /testbed
