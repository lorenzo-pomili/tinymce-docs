### `autosave_interval`

This option enables you to specify the time the editor should wait between taking snapshots of the current content and saving them to local storage. The syntax is to append the letter `s` to the end of a number value. For example, "30s" for 30 seconds.

**Type**: `String`

**Default Value:** `'30s'`

#### Example: Using `autosave_interval`

```js
tinymce.init({
  selector: 'textarea',  // change this value according to your HTML
  autosave_interval: '20s'
});
```
