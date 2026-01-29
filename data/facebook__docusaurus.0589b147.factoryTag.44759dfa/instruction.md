# Bug Report

### Describe the bug

I'm experiencing an issue with MDX JSX attribute parsing where quoted attribute values are not being recognized correctly. When I try to use standard JSX attributes with quoted strings, the parser seems to fail or produce unexpected results.

### Reproduction

```jsx
<Component name="value" />
```

When parsing the above JSX in MDX, the closing quote of the attribute value doesn't seem to be matched properly. It's like the parser is looking for the wrong character code to close the quoted string.

### Expected behavior

The parser should correctly recognize and parse JSX attributes with quoted values (both single and double quotes). The opening and closing quotes should match and the attribute value should be extracted correctly.

### Additional context

This seems to affect any JSX element with quoted attribute values in MDX content. The issue appears to be related to how the parser handles the closing quote marker when processing attribute values.

---
Repository: /testbed
