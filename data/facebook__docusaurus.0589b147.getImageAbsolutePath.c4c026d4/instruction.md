# Bug Report

### Bug: Images with @site/ alias not resolving correctly

I'm experiencing an issue where images referenced using the `@site/` alias are failing to load properly in my MDX files. The image paths seem to be getting mangled during processing.

### Reproduction

In an MDX file, when I try to reference an image using the `@site/` alias:

```md
![My Image](@site/static/img/my-image.png)
```

The image fails to load. Looking at the console, it appears the path is being resolved incorrectly.

### Expected behavior

Images using the `@site/` prefix should resolve correctly to the site directory. For example, `@site/static/img/my-image.png` should resolve to the correct absolute path based on the site's root directory.

### Additional context

This was working fine in previous versions. It seems like something changed in how the `@site/` alias is being processed. The path resolution logic might not be handling the alias replacement properly anymore.

---
Repository: /testbed
