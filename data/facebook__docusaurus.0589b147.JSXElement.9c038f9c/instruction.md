# Bug Report

### Describe the bug

I'm experiencing an issue with the `<Translate>` component where whitespace-only JSX text nodes are not being filtered out correctly during translation extraction. This causes problems when the component has formatting/indentation around its content.

### Reproduction

```jsx
<Translate id="my-translation" description="A sample translation">
  
  Hello World
  
</Translate>
```

When the `<Translate>` component has whitespace or newlines around the actual text content (which is common with JSX formatting), the translation extraction doesn't handle it properly. The whitespace nodes should be ignored, but they seem to interfere with the extraction process.

### Expected behavior

The translation extractor should ignore empty/whitespace-only JSX text nodes and only extract the actual meaningful text content. The formatting and indentation of JSX code shouldn't affect how translations are extracted.

### Additional context

This becomes especially problematic when:
1. Using prettier or other formatters that add newlines/indentation
2. Wrapping `<Translate>` content across multiple lines for readability
3. Having nested JSX elements within the translate component

The extraction should be resilient to JSX formatting variations and only care about the actual content.

---
Repository: /testbed
