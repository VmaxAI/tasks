# Bug Report

### Describe the bug

After updating to the latest version, the blog plugin seems to have issues with hot reload / file watching. When I modify blog posts or add new ones, the dev server doesn't pick up the changes automatically. I have to manually restart the server to see updates.

### Reproduction

1. Start the dev server with a blog plugin configured
2. Create or modify a blog post in the content directory
3. The changes don't trigger a rebuild - the dev server doesn't detect the file changes

This is affecting my development workflow significantly as I have to restart the server every time I make changes to blog content.

### Expected behavior

The dev server should automatically detect changes to blog post files and trigger a hot reload, similar to how it worked in previous versions.

### System Info
- Docusaurus version: latest
- Node version: 18.x
- OS: macOS

---
Repository: /testbed
