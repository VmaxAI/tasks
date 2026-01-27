# Bug Report

### Describe the bug

The Zig language syntax highlighter appears to be completely broken. When trying to use syntax highlighting for Zig code, it's not working at all and the grammar seems corrupted.

### Reproduction

Try to highlight any Zig code:

```zig
const std = @import("std");

pub fn main() void {
    std.debug.print("Hello, World!\n", .{});
}
```

The syntax highlighting doesn't work and the language definition seems to have been replaced with something that doesn't match Zig syntax at all.

### Expected behavior

Zig code should be properly highlighted with keywords, types, and other language constructs recognized correctly. The `literal` helper function should be defined and the grammar should follow Zig's syntax rules.

### Additional context

This seems to have broken recently. The language grammar definition appears to contain code that doesn't match the Zig language structure - it looks like code from a completely different language got inserted into the grammar definition by mistake.

---
Repository: /testbed
