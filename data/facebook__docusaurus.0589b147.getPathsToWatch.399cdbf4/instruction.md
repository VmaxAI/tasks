# Bug Report

### Describe the bug

After updating to the latest version, the blog plugin is not watching markdown files correctly. Changes to blog posts don't trigger hot reload anymore, and I have to manually restart the dev server every time I make an edit to a blog post.

### Reproduction

1. Set up a Docusaurus site with the blog plugin
2. Configure the blog with multiple content paths or include patterns
3. Start the dev server
4. Make changes to a blog post markdown file
5. The dev server doesn't detect the changes and hot reload doesn't work

### Expected behavior

The dev server should detect changes to blog post files and automatically reload the page when markdown files are edited, just like it did in previous versions.

### System Info
- Docusaurus version: latest
- Node version: 18.x
- OS: macOS

---
Repository: /testbed
