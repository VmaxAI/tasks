# Bug Report

### Describe the bug

I'm experiencing an issue where export statements in MDX files are not being parsed correctly. It seems like `const` and `var` exports are being rejected or not recognized properly, even though they should be valid JavaScript/MDX syntax.

### Reproduction

```mdx
export const metadata = {
  title: 'My Page',
  description: 'Page description'
}

# My Content
```

When trying to use this in an MDX file, the export statement with `const` doesn't seem to be parsed/recognized as it should be. The same issue occurs with `var` declarations.

### Expected behavior

Export statements using `const`, `var`, `class`, and `function` keywords should all be parsed and handled correctly in MDX files. These are all valid JavaScript export patterns that should work.

### System Info
- @mdx-js/mdx version: 3.0.0

---
Repository: /testbed
