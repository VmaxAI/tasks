# Bug Report

### Describe the bug

There's an issue with the broken links warning message that appears when Docusaurus detects frequent broken links across multiple pages. The message text is getting corrupted/truncated and appears incomplete.

### Reproduction

1. Set up a Docusaurus site with broken links that appear on multiple pages (e.g., in the navbar or footer)
2. Ensure the same broken link appears more than 5 times across different pages
3. Run the build process
4. Check the error/warning message output

### Expected behavior

The warning message should display properly formatted text like:
```
It looks like some of the broken links we found appear in many pages of your site.
Maybe those broken links appear on all pages through your site layout?
We recommend that you check your theme configuration for such links (particularly, theme navbar and footer).
Frequent broken links are linking to: [list of links]
```

### Actual behavior

The message appears with missing characters at the beginning of some lines:
```
  looks like some of the broken links we found appear in many pages of your site.
 ybe those broken links appear on all pages through your site layout?
  recommend that you check your theme configuration for such links (particularly, theme navbar and footer).
 equent broken links are linking to: [list of links]
```

The words "It", "Ma", "We", and "Fr" are missing from the start of their respective lines, making the message look broken and unprofessional.

This makes it harder to understand what the warning is trying to communicate, especially for users who might be seeing this error for the first time.

---
Repository: /testbed
