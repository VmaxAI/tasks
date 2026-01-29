# Bug Report

### Describe the bug

I'm experiencing an issue with the blog plugin's author validation. When I provide a valid authors map in my blog configuration, the plugin throws an error instead of accepting it. Conversely, when I provide an invalid authors map, it seems to be accepted without any validation errors.

### Reproduction

```js
// In docusaurus.config.js or blog plugin options
{
  authorsMapPath: './authors.yml'
}
```

```yaml
# authors.yml - Valid authors map
john_doe:
  name: John Doe
  title: Software Engineer
  url: https://github.com/johndoe
  image_url: https://github.com/johndoe.png
```

When I run the build with a perfectly valid authors configuration like above, I get validation errors thrown. However, if I intentionally provide malformed data, it doesn't catch the errors as expected.

### Expected behavior

The plugin should:
1. Accept valid authors map configurations without throwing errors
2. Reject invalid authors map configurations with appropriate validation errors

### System Info

- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
