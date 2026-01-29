# Bug Report

### Describe the bug

I'm experiencing an issue where the blog plugin fails to load content properly. It seems like there's a problem during the content loading phase that prevents the blog from being built correctly.

### Reproduction

When running a Docusaurus build with the blog plugin enabled, the build process fails during the content loading step. This happens with a standard blog configuration:

```js
{
  plugins: [
    [
      '@docusaurus/plugin-content-blog',
      {
        routeBasePath: 'blog',
        postsPerPage: 10,
        blogTitle: 'My Blog',
        blogDescription: 'A blog about things',
      },
    ],
  ],
}
```

The error occurs even with valid blog posts in the content directory. The build was working fine before, but now it consistently fails when trying to load blog content.

### Expected behavior

The blog plugin should successfully load all blog posts and generate the necessary routes for the blog list, individual posts, and tag pages without errors.

### System Info
- Docusaurus version: latest
- Node version: 18.x
- OS: macOS

---
Repository: /testbed
