# Bug Report

### Describe the bug

After a recent update, the `<head>` component in MDX files is not being recognized correctly. The component seems to be looking for the wrong element type and matching against node names incorrectly.

### Reproduction

Create an MDX file with a `<head>` component:

```mdx
# My Page

<head>
  <meta name="description" content="test" />
</head>

Some content here.
```

The `<head>` component is not being transformed to `<Head>` as expected. Additionally, any element containing "head" in its name (like `<header>` or `<subheader>`) might be incorrectly matched and transformed.

### Expected behavior

- Only the exact `<head>` component should be transformed to `<Head>`
- The component should work with flow elements (block-level) as it did before
- Elements like `<header>` or `<subheader>` should not be affected

### System Info
- Docusaurus version: latest
- MDX loader affected

---
Repository: /testbed
