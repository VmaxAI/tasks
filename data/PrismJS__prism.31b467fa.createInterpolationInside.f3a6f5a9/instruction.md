# Bug Report

### Describe the bug

C# string interpolation format strings are not being highlighted correctly. The format specifiers (like `:D`, `:C2`, `:0.00`, etc.) that come after the colon in interpolated strings are not being recognized as format strings.

### Reproduction

```csharp
// Format strings in interpolations should be highlighted
var price = 123.45;
var formatted = $"Price: {price:C2}";
var date = DateTime.Now;
var dateStr = $"Date: {date:yyyy-MM-dd}";
```

The part after the colon (`:C2`, `:yyyy-MM-dd`) should be tokenized as format-string but it's being treated as part of the expression instead.

### Expected behavior

Format specifiers in C# interpolated strings should be properly highlighted/tokenized as `format-string` tokens. The colon and everything after it (up to the closing brace) should be recognized as the format string portion of the interpolation.

### System Info
- Prism version: latest
- Language: C# (csharp)

---
Repository: /testbed
