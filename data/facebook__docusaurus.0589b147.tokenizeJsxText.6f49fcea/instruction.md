# Bug Report

### Describe the bug

I'm experiencing an issue with MDX JSX text tag parsing where the token types appear to be assigned incorrectly. When parsing JSX text tags, certain attributes and name components seem to be getting misidentified or processed in the wrong order.

### Reproduction

```jsx
<Component member.property="value" namespace:local="test" />
```

When parsing JSX text tags with member notation (e.g., `member.property`) or namespaced attributes (e.g., `namespace:local`), the tokenizer doesn't correctly identify the token types. The member markers and attribute name components appear to be swapped or out of order.

### Expected behavior

The tokenizer should correctly identify and assign token types to:
- Member markers in tag names (`mdxJsxTextTagNameMemberMarker`)
- Member names (`mdxJsxTextTagNameMember`)
- Attribute name locals (`mdxJsxTextTagAttributeNameLocal`)
- Attribute value literal markers and values

Each component should be tokenized in the correct sequence and with the appropriate type identifier.

### System Info
- MDX version: 3.0.0
- Parser: micromark-extension-mdx-jsx

This seems to have broken after a recent update. The token sequence doesn't match what's expected for proper JSX parsing.

---
Repository: /testbed
