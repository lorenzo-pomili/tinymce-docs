### `rtc_server_disconnected`

If the RTC session fails to connect, or is disconnected due to an error, the user will be blocked from editing (using [setProgressState]({{site.baseurl}}/api/tinymce/tinymce.editor/#setprogressstate)) along with an error notification:

<img alt="warning icon" src="{{ site.baseurl }}/images/icons/warning.svg" style="vertical-align:middle;"/>**RTC has lost connection to the server, please reload the page. More information may be available in the console.**

![RTC disconnected error example]({{site.baseurl}}/images/rtc-error-example.png "RTC disconnected error example")

The `rtc_server_disconnected` callback can be used to provide an alternative response to this condition.

> **Caution**: It is critical to at least handle the `client_update_required` reason. This indicates the RTC plugin in the current editor instance is out-of-date compared to other users on the session. The behavior in this scenario depends on the configuration:
> * If the `rtc_server_disconnected` is set, no message is displayed to the user for this error. It is up to the integrator to manage cleanly reloading the page.
> * If the `rtc_server_disconnected` is not set, the suggested error message will be displayed in a notification asking the user to reload the page.

{% if plugincode != "rtc" %}
Required plugin
: [Real-Time Collaboration (`rtc`)]({{site.baseurl}}/plugins/premium/rtc/)
{% endif %}

Type
: Function (Returns a [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise))

Input parameters
: | Field | Type | Description |
|-------|:----:|-------------|
| `reason` | `string` | The cause of the disconnection. The value will be one of the reasons described below. |
| `message` | `string` | A suggested description for the error, translated into the active user interface language, suitable for displaying to a user. This string may contain HTML, and in some cases is the same string displayed in the editor notification. |

#### Reasons for disconnection

The `reason` field will have one of the following values.

`client_update_required`
: This error indicates the RTC plugin is out-of-date and cannot connect to an active session for the supplied `rtc_document_id`. This can happen on startup, but is more common at runtime during editor upgrades. The suggested message recommends the user reload the page.

`encryption`
: Indicates a failure at startup either: in the cryptography process or the configured `rtc_encryption_provider` function. This may be caused by an error in the editor configuration.

`jwt`
: Indicates a problem with the configured `rtc_token_provider` function. Either the provider returned a rejected promise, the returned object structure was incorrect, or the token was invalid.

`content`
: Indicates a problem with the configured `rtc_initial_content_provider` function. Either the provider returned a rejected promise or the returned object structure was incorrect.

`general`
: A generic error for reasons that do not yet have a category. Details will be printed to the browser console.

#### Example of handling server disconnection

```js
tinymce.init({
  selector: 'textarea', // change this value according to your HTML
  plugins: 'rtc',
  rtc_document_id: 'unique-document-id',
  rtc_encryption_provider: () => Promise.resolve({ key: 'a secret key' }),
  rtc_token_provider: () => Promise.resolve({ token: 'signed-JWT-token' }),
  rtc_server_disconnected: ({ reason, message }) => {
    // perform some action in response to the RTC session disconnecting, such as:
    tinymce.activeEditor.notificationManager.open({
      text: 'Disconnected: ' + reason + '\n' + message,
      type: 'error'
    });
  }
});
```