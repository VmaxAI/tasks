# Bug Report

### Describe the bug

I'm experiencing an issue with MDX import/export statement parsing. After a recent update, MDX files with `import` or `export` statements are not being parsed correctly. The parser seems to be failing to recognize valid ES module syntax.

### Reproduction

```mdx
import Component from './Component'
export const meta = { title: 'Example' }

# My Content
```

When processing this MDX file, the import and export statements are not being recognized properly. The parser appears to be looking for the wrong character code after the keywords.

### Expected behavior

Valid `import` and `export` statements should be parsed correctly and the MDX content should render without issues. The ES module syntax should be properly tokenized.

### Additional context

This seems to affect all MDX files that use ES module imports/exports at the top of the file. The issue appears to be in the tokenization logic for detecting these keywords.

---
Repository: /testbed
