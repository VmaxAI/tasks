# Bug Report

### Describe the bug

The baseUrl issue banner is displaying incorrect information when Docusaurus fails to load properly. The banner shows "(default value)" next to the baseUrl when it's NOT the default value ("/"), which is backwards. Additionally, the suggested baseUrl is not appearing in the banner because it's trying to insert into an element with the wrong ID.

### Reproduction

1. Set up a Docusaurus site with a non-default baseUrl (e.g., `/docs/`)
2. Deploy the site to a location that doesn't match the configured baseUrl
3. Navigate to the site - the error banner should appear
4. Observe that the banner incorrectly shows "(default value)" next to `/docs/`
5. Notice that the suggested baseUrl field is empty

### Expected behavior

- The "(default value)" text should only appear when baseUrl is actually "/" (the default)
- The suggested baseUrl should be displayed in the banner correctly

### System Info
- Docusaurus version: latest
- Browser: Any

---
Repository: /testbed
