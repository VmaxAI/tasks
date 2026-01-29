# Bug Report

### Describe the bug

The active document detection is not working properly when navigating between docs pages. The sidebar doesn't highlight the current page, and the version dropdown doesn't show the correct alternate versions for the current document.

### Reproduction

1. Create a docs site with multiple versions
2. Navigate to any documentation page
3. Observe that the sidebar doesn't highlight the active page
4. Check the version dropdown - alternate versions are missing or incorrect

For example, when visiting `/docs/getting-started`, the page renders correctly but:
- The sidebar item for "Getting Started" is not marked as active
- The version dropdown doesn't show links to the same page in other versions

### Expected behavior

- The current page should be highlighted in the sidebar
- The version dropdown should display links to the same document across all available versions
- Navigation state should properly reflect the active document

### System Info
- Docusaurus version: latest
- Node version: 18.x

This seems to have broken recently, as it was working fine before. The page content loads correctly, but the navigation state is completely off.

---
Repository: /testbed
