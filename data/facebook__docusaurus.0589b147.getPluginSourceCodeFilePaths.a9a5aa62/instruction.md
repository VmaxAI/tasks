# Bug Report

### Describe the bug

When extracting translations from plugin source code, the paths are being resolved incorrectly. It seems like the code is using `themePath` to resolve all plugin code paths instead of using the plugin's base path. This causes translation extraction to fail or look in the wrong directories.

### Reproduction

I noticed this when trying to extract translations from a custom plugin. The translation extractor can't find the source files properly.

Steps to reproduce:
1. Create a plugin with source code in its plugin directory
2. The plugin has `getPathsToWatch()` that returns paths relative to the plugin directory
3. Try to extract translations
4. The paths get resolved relative to the theme path instead of the plugin path

For example, if a plugin is located at `/project/plugins/my-plugin` and returns paths like `['src/components']`, these should resolve to `/project/plugins/my-plugin/src/components`, but instead they're being resolved relative to the theme path.

### Expected behavior

Plugin source code paths should be resolved relative to the plugin's base path (`plugin.path`), not relative to the theme path. The theme path should only be used for resolving the theme path itself.

### Additional context

This appears to affect any plugin that has both `getPathsToWatch()` and `getThemePath()` defined. The translation extraction won't work correctly for the plugin's own source files.

---
Repository: /testbed
