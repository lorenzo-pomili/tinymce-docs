### `a11ychecker_ignored_rules`

The `a11ychecker_ignored_rules` option prevents specific Accessibility Checker rules from being checked. This feature allows developers to skip rules that they do not wish to check. For example: To skip rules that flag known content issues or custom HTML that should not be checked.

**Type:** A comma-separated string.

**Default Value:** `''`

**Possible values:** `'D1'`, `'D2'`, `'D3'`, `'D4O'`, `'D4U'`, `'D5A'`, `'D5B'`, `'D5C'`, `'H93'`, `'I1'`, `'I2'`, `'T1'`, `'T2'`, `'T3'`, `'T4A'`, `'T4B'`, `'T4C'`

#### Example: Using `a11ychecker_ignored_rules`

This examples shows how to ignore the following checks (rules):

* D2 - Sequential headings
* I2 - Image `alt` text is not the image filename
* T4B - Table headers

```js
tinymce.init({
  selector: 'textarea',  // change this value according to your html
  plugins: 'a11ychecker',
  toolbar: 'a11ycheck',
  a11ychecker_ignored_rules: 'D2, I2, T4B'
});
```

