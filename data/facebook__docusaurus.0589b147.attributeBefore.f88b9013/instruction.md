# Bug Report

### Describe the bug

I'm encountering an issue with self-closing JSX tags in MDX. When using a self-closing tag (with `/>` syntax), the parser seems to be processing it incorrectly and the tag doesn't render as expected.

### Reproduction

```jsx
<MyComponent />
```

When I use this self-closing tag syntax in my MDX file, it's not being parsed correctly. The component either doesn't render at all or throws an error during parsing.

### Expected behavior

Self-closing JSX tags should be properly recognized and parsed. The component should render normally just like it would in regular JSX/React code.

### Additional context

This seems to have started happening recently. Regular non-self-closing tags like `<MyComponent></MyComponent>` work fine, but the self-closing syntax specifically is causing problems.

---
Repository: /testbed
