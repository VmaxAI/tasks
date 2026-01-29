# Bug Report

### Describe the bug

The table of contents (TOC) is no longer showing level 2 headings (h2/##). After a recent update, only h3 and deeper headings appear in the TOC, but h2 headings are being excluded.

### Reproduction

Create a markdown file with headings at different levels:

```md
# Page Title

## Section 1
Some content here

## Section 2
More content

### Subsection 2.1
Details
```

**Expected:** The TOC should include "Section 1", "Section 2", and "Subsection 2.1"

**Actual:** The TOC only shows "Subsection 2.1", the h2 headings are missing

### Expected behavior

Level 2 headings (h2/##) should be included in the table of contents. The TOC should start from h2 and include all deeper levels (h3, h4, etc.), with only the h1 title being excluded.

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
