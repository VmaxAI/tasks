# Bug Report

### Describe the bug

I'm experiencing an issue with broken link detection for anchor links. It seems like the validator is incorrectly reporting anchor links as broken when they actually exist on the target page.

### Reproduction

When I have a markdown file with links like:

```markdown
[Link to section](#my-section)

## My Section
```

Or links between pages:

```markdown
[Link to other page](/docs/page#some-anchor)
```

The build process reports these as broken links even though the anchors are valid and exist on the target pages.

### Expected behavior

Valid anchor links should not be reported as broken. The link checker should:
1. Detect when a link has a hash/anchor
2. Find the target page
3. Check if that anchor exists on the page
4. Only report it as broken if the anchor doesn't exist

Currently it seems to be doing the opposite - reporting valid anchors as broken.

### System Info

- Docusaurus version: latest
- Node version: 18.x

This is blocking our documentation builds. Any help would be appreciated!

---
Repository: /testbed
