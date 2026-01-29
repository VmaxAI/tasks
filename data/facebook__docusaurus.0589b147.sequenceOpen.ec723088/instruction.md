# Bug Report

### Describe the bug

I'm encountering an issue with ATX heading parsing in MDX. When I have headings with spaces in the sequence (like `# # #` or similar patterns), they're being incorrectly parsed or accepted when they shouldn't be.

### Reproduction

```markdown
# # # This should not be a valid heading
## # Invalid heading with space
### ## Mixed heading markers
```

These malformed headings with spaces between the `#` characters are being processed when they should be rejected as invalid syntax.

### Expected behavior

ATX headings should only accept consecutive `#` characters without spaces. For example:
- `# Heading` ✓ (valid)
- `## Heading` ✓ (valid)
- `# # Heading` ✗ (should be invalid)

The parser should reject headings that have spaces within the opening sequence of hash marks.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: Latest

---
Repository: /testbed
