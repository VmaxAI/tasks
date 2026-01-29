# Bug Report

### Describe the bug

I'm experiencing an issue with MDX parsing where certain constructs are not being resolved correctly. It seems like the resolver functions are being skipped during the parsing process, which causes some markdown/MDX features to not work as expected.

### Reproduction

When using MDX with multiple constructs that have `resolveAll` functions, the resolvers don't seem to be executing properly. This affects things like link references, footnotes, and other constructs that need post-processing.

Example MDX content that fails to parse correctly:
```mdx
[link][ref]

[ref]: https://example.com
```

The link reference doesn't get resolved and remains as raw text instead of being converted to a proper link.

### Expected behavior

All constructs with `resolveAll` functions should be processed in order, and features like link references should work correctly. The resolver should be called for each unique construct that defines one.

### Additional context

This seems to have started happening recently. I noticed that some markdown features that rely on the resolveAll phase are no longer working. The parsing completes without errors, but the output is incorrect.

---
Repository: /testbed
