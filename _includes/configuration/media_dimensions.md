### `media_dimensions`

This options allows you disable the `Dimensions` input fields in the media dialog.

**Type:** `Boolean`

**Default Value:** `true`

**Possible Values:** `true`, `false`

#### Example: Using `media_dimensions`

```js
tinymce.init({
  selector: 'textarea',  // change this value according to your HTML
  plugins: 'media',
  menubar: 'insert',
  toolbar: 'media',
  media_dimensions: false
});
```

