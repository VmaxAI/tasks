# Bug Report

### Describe the bug

C# string interpolation is not being highlighted correctly. When using interpolated strings with curly braces, the syntax highlighting breaks and the interpolation expressions are not properly recognized.

### Reproduction

```csharp
// This interpolation is not being highlighted correctly
var message = $"Hello {name}";

// More complex interpolations also fail
var formatted = $"Value: {value:C2}";
```

The curly braces and expressions inside interpolated strings aren't being tokenized properly, causing the entire string to be highlighted incorrectly.

### Expected behavior

The interpolation expressions (content within `{` and `}`) should be properly highlighted as C# code, with format strings (like `:C2`) being recognized as separate tokens.

### System Info
- Prism version: latest
- Language: C#

---
Repository: /testbed
