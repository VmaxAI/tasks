# Bug Report

### Describe the bug

I'm experiencing an issue with the `<Translate>` component where whitespace handling seems broken. When I format my JSX code with multiple lines and indentation (which is normal in any real codebase), the translation extraction appears to be incomplete or failing.

### Reproduction

```jsx
<Translate id="my-translation" description="A helpful description">
  This is my translation message
</Translate>
```

When the component is formatted like above (with newlines and indentation), the translation doesn't seem to be processed correctly. It worked fine before when everything was on a single line, but that's not practical for longer messages or when using code formatters.

### Expected behavior

The `<Translate>` component should handle multi-line content properly, ignoring formatting whitespace while still extracting the translation message. Code formatting shouldn't break translation extraction.

### System Info
- Docusaurus version: latest
- Node version: 18.x

This is causing issues in our documentation because we can't format our code properly without breaking translations. Any help would be appreciated!

---
Repository: /testbed
