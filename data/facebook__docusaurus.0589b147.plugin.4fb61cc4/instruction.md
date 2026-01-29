# Bug Report

### Describe the bug

Footnote references and definitions are not linking correctly in blog posts. When clicking on a footnote reference, it doesn't jump to the corresponding footnote definition, and the IDs don't match up properly.

### Reproduction

Create a blog post with footnotes:

```markdown
This is some text with a footnote[^1].

[^1]: This is the footnote content.
```

When rendered, the footnote reference link and the footnote definition have mismatched IDs. The reference might have the suffix appended correctly, but the definition has the suffix in the wrong position, causing the link to break.

### Expected behavior

Clicking on a footnote reference (e.g., `[^1]`) should jump to the corresponding footnote definition at the bottom of the page. The IDs should match between the reference and definition.

### Additional context

This seems to affect how the hash suffix is being applied to footnote identifiers. The reference and definition end up with different ID formats, preventing them from linking to each other properly.

---
Repository: /testbed
