# Bug Report

### Describe the bug

I'm experiencing an issue with nested MDX JSX tags where the tag stack gets reset incorrectly, causing child tags to not be properly tracked. When using nested JSX components in MDX content, the parser seems to lose track of the parent-child relationship between tags.

### Reproduction

```mdx
<Outer>
  <Inner>
    Content here
  </Inner>
</Outer>
```

When parsing the above MDX with nested JSX tags, the inner tag is not properly associated with its parent. The tag stack appears to be getting cleared when it shouldn't be, which breaks the nesting structure.

### Expected behavior

Nested JSX tags should maintain their parent-child relationships in the tag stack. Each new tag should be pushed onto the existing stack rather than replacing it entirely.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

This seems to be affecting any MDX content with nested JSX components. The issue manifests when the parser enters a new JSX tag while already inside another one.

---
Repository: /testbed
