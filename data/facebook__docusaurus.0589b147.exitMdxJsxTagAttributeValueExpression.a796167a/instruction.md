# Bug Report

### Describe the bug

I'm encountering an issue with MDX JSX attribute value expressions. When using expression values in JSX attributes, the value is being assigned to the wrong attribute or the estree data is not being attached correctly.

### Reproduction

```jsx
<Component attr1="value1" attr2={expression} />
```

When parsing the above MDX, the expression value seems to be assigned to the wrong attribute. It looks like the parser is picking up an incorrect attribute from the attributes array.

Also noticed that estree data might not be getting attached to the node when it should be - the condition for adding estree seems inverted.

### Expected behavior

The expression value should be correctly assigned to `attr2`, and any estree data from the token should be properly attached to the node.

### Additional context

This affects any MDX content that uses JSX expressions as attribute values. The parsed AST doesn't match the actual structure of the JSX tags.

---
Repository: /testbed
