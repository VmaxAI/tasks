# Bug Report

### Describe the bug

After a recent update, PHP syntax highlighting is completely broken. The code is not being highlighted at all, and it appears that the language definition is incomplete or cut off.

### Reproduction

```php
<?php
function test() {
    $variable = "hello";
    return $variable;
}
?>
```

When trying to highlight the above PHP code, nothing is highlighted. The syntax highlighting doesn't work for any PHP code - variables, functions, keywords, etc. all appear as plain text.

### Expected behavior

PHP code should be properly syntax highlighted with:
- Keywords (function, return, etc.) highlighted
- Variables ($variable) highlighted  
- Strings highlighted
- Delimiters (<?php, ?>) highlighted

The highlighting was working fine in the previous version but stopped working after the latest update.

### System Info
- Language: PHP
- Version: Latest

---
Repository: /testbed
