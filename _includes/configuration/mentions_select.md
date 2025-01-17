### `mentions_select`

This option enables a hover card to be presented when a user hovers over a mention in {{site.productname}}. This could include details about the user. A custom hover card HTML element can be provided or a predefined template can be specified.

**Type:** `Function`

#### Example: Using `mentions_select`

```js
var userRequest = {};
tinymce.init({
  selector: 'textarea',
  plugins: 'mentions',
  mentions_selector: 'span.mymention',
  mentions_menu_complete: function (editor, userInfo) {
    var span = editor.getDoc().createElement('span');
    span.className = 'mymention';
    span.setAttribute('data-mention-id', userInfo.id);
    span.appendChild(editor.getDoc().createTextNode('@' + userInfo.name));
    return span;
  },
  mentions_select: function (mention, success) {
    // `mention` is the element we previously created with `mentions_menu_complete`
    // in this case we have chosen to store the id as an attribute
    var id = mention.getAttribute('data-mention-id');
    // request more information about the user from the server and cache locally
    if (!userRequest[id]) {
      userRequest[id] = fetch('/user?id=' + id);
    }
    userRequest[id].then(function(userDetail) {
      var div = document.createElement('div');
      div.innerHTML = (
        '<div>' +
        '<h1>' + userDetail.fullName + '</h1>' +
        '<img src="' + userDetail.image + '" ' +
            'style="width: 50px; height: 50px; float: left;"/>' +
        '<p>' + userDetail.description + '</p>' +
        '</div>'
      );
      success(div);
    });
  }
});
```

#### `mentions_select` with predefined templates

{{site.requires_5_6v}}

If `mentions_select` is resolved with an object specifying the type and user details, a predefined hover card template will be used. To use the predefined template, set `type` to `'profile'`. For details on the user properties required for the `profile` template, see: [User properties](#userproperties).

##### Example: Using the `'profile'` template with `mentions_select`

```js
var userRequest = {};
tinymce.init({
  selector: 'textarea',
  plugins: 'mentions',
  mentions_selector: 'span.mymention',
  mentions_menu_complete: function (editor, userInfo) {
    var span = editor.getDoc().createElement('span');
    span.className = 'mymention';
    span.setAttribute('data-mention-id', userInfo.id);
    span.appendChild(editor.getDoc().createTextNode('@' + userInfo.name));
    return span;
  },
  mentions_select: function (mention, success) {
    // `mention` is the element we previously created with `mentions_menu_complete`
    // in this case we have chosen to store the id as an attribute
    var id = mention.getAttribute('data-mention-id');
    // request more information about the user from the server and cache locally
    if (!userRequest[id]) {
      userRequest[id] = fetch('/user?id=' + id);
    }
    userRequest[id].then(function(userDetail) {
      success({ type: 'profile', user: userDetail });
    });
  }
});
```
