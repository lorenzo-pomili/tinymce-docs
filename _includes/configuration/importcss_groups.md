### `importcss_groups`

This option enables group matching selectors into submenus in the `Formats` menu dropdown. You can use a `string`, `regexp` or a `function` to filter selectors. You can also omit the filter to get all non-matching ones into a specific group. You can also specify a group specific `selector_converter` so that formats for a specific group are produced by that converter.

#### Example using a string filter with `importcss_groups`

```js
tinymce.init({
  selector: 'textarea',  // change this value according to your HTML
  plugins: 'importcss',
  menubar: 'format',
  content_css: '/my-styles.css',
  importcss_groups: [
    {title: 'Table styles', filter: /^(td|tr)\./}, // td.class and tr.class
    {title: 'Block styles', filter: /^(div|p)\./}, // div.class and p.class
    {title: 'Other styles'} // The rest
  ]
});
```

