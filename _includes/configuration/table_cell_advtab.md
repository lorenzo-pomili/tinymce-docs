### `table_cell_advtab`

This option makes it possible to disable the advanced tab in the table cell dialog box. The advanced tab allows a user to input `style`, `border color` and `background color` values.

**Type:** `Boolean`

**Default Value:** `true`

**Possible Values:** `true`, `false`

#### Example: Using `table_cell_advtab`

```js
tinymce.init({
  selector: 'textarea',  // change this value according to your HTML
  plugins: 'table',
  menubar: 'table',
  toolbar: 'table',
  table_cell_advtab: false
});
```

