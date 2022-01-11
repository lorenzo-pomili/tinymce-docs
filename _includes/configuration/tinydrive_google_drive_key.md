### `tinydrive_google_drive_key`

This option sets the Google Drive API key for integrating Google Drive into {{site.cloudfilemanager}}. For information on how to generate this key, refer to the [Google Drive integration guide]({{site.baseurl}}/plugins-ref/premium/tinydrive/integrations/googledrive-integration/).

Type
: `string`

#### Example: Using `tinydrive_google_drive_key`

```js
tinymce.init({
  selector: 'textarea',  // change this value according to your HTML
  plugins: 'tinydrive',
  tinydrive_google_drive_key: '<your google drive api key>'
});
```