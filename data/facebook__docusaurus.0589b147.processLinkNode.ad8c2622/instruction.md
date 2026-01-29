# Bug Report

### Describe the bug

Links to `.md` and `.mdx` files are no longer being processed correctly by the MDX loader. After a recent change, markdown links that should be transformed are being skipped, causing broken links in the generated documentation.

### Reproduction

Create a markdown file with a link to another markdown file:

```md
# My Doc

Check out [this other page](./other-page.md) for more info.
```

The link to `./other-page.md` is not being transformed as expected. The same issue occurs with `.mdx` files:

```md
See [advanced guide](../guides/advanced.mdx) for details.
```

### Expected behavior

Links to `.md` and `.mdx` files should be processed and transformed by the link transformer, just like they were before. These links should resolve correctly in the built documentation.

### System Info
- Docusaurus version: latest
- Node version: 18.x

This seems to have broken recently - links to markdown files were working fine in previous versions.

---
Repository: /testbed
