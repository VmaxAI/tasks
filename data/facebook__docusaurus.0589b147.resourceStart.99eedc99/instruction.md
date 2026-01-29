# Bug Report

### Describe the bug

I'm encountering an issue with link parsing in markdown. When I try to parse markdown links with resources (URLs), the parser seems to be failing or producing incorrect output. The links aren't being recognized properly.

### Reproduction

```js
const markdown = '[example](https://example.com)'
const result = parse(markdown)
// Link is not parsed correctly
```

Also happens with:
```markdown
[link text](http://url.com)
[another link](/path/to/page)
```

### Expected behavior

Links with resources should be parsed correctly and the AST should contain proper link nodes with the URL information preserved.

### Additional context

This seems to have started recently. The parser was working fine before with these same markdown inputs. Not sure what changed but links are definitely broken now.

---
Repository: /testbed
