# Bug Report

### Describe the bug

The Stylus language grammar definition appears to be incomplete or corrupted. When trying to use Stylus syntax highlighting, the grammar object is cut off mid-definition and doesn't contain the expected token patterns.

### Reproduction

Try to use Stylus syntax highlighting with code like:

```stylus
body
  font-size 14px
  color #333
  
.container
  margin 0 auto
  width 100%
```

The syntax highlighting doesn't work properly - tokens aren't being recognized and the code appears unstyled or incorrectly styled.

### Expected behavior

The Stylus grammar should include complete definitions for all token types including:
- Comments (single-line and multi-line)
- URLs
- Strings and interpolation
- Functions
- Keywords
- Colors (hex codes, named colors, rgb/rgba, hsl/hsla)
- Numbers and units
- And other Stylus-specific syntax

The grammar definition seems to be truncated and missing most of its implementation.

### Additional context

This might have been introduced during a recent refactoring or merge. The grammar function is missing the complete token definitions that should be present for proper Stylus syntax highlighting.

---
Repository: /testbed
