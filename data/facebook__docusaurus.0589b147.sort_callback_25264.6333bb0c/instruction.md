# Bug Report

### Describe the bug
After a recent update, I'm seeing inconsistent ordering of component declarations in the generated MDX output. The components are being sorted in reverse alphabetical order instead of the expected alphabetical order.

### Reproduction
When processing MDX content with multiple invalid component names, the generated variable declarations appear in the wrong order.

For example, if I have components that need to be renamed (like `foo-bar`, `baz-qux`, `alpha-beta`), they're being declared in reverse order (`foo-bar`, `baz-qux`, `alpha-beta`) instead of alphabetical order (`alpha-beta`, `baz-qux`, `foo-bar`).

This seems to affect the consistency of generated output and makes diffs harder to review since the order changes unpredictably.

### Expected behavior
Component declarations should be sorted in alphabetical order (A-Z) for consistent and predictable output.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: Latest

---
Repository: /testbed
