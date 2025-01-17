### `mentions_fetch`

This option lets you request a list of users from your server that match a search query. The callback gets passed two parameters: one is the search query object, the other is the success callback to execute with the results. The query object has a term property that contains what the user has typed after the "@" sign. The success call should contain an array of users. For information on the user properties to pass the success callback for the available mentions item types (`mentions_item_type`), see: [User properties](#userproperties).

**Type:** `Function`

#### Example: Using `mentions_fetch`

```js
var usersRequest = null;
tinymce.init({
  selector: 'textarea',
  plugins: 'mentions',
  mentions_fetch: function (query, success) {
    // Fetch your full user list from the server and cache locally
    if (usersRequest === null) {
      usersRequest = fetch('/users');
    }
    usersRequest.then(function(users) {
      // query.term is the text the user typed after the '@'
      users = users.filter(function (user) {
        return user.name.indexOf(query.term.toLowerCase()) !== -1;
      });

      users = users.slice(0, 10);

      // Where the user object must contain the properties `id` and `name`
      // but you could additionally include anything else you deem useful.
      success(users);
    });
  }
});
```

The `success` callback can be passed an optional array of extra items. When clicked, the menu reloads and passes additional query parameters to the fetch function. The extra items can be used to search with different queries or show additional results, such as a full text search (which is slower to fetch). Each extra item should contain:

* A "text" property for the content to be displayed in the menu.
* A "meta" property for that will be passed using the fetch query parameter.

#### Example with extras

```js
tinymce.init({
  selector: 'textarea',
  plugins: 'mentions',
  mentions_fetch: function (query, success) {
    // query.term is the text the user typed after the '@'
    var url = '/users?query=' + query.term;
    var isFullTextSearch = query.meta && query.meta.fullTextSearch;
    if (isFullTextSearch) {
      url += '&full=true'
    }

    // Extras are shown at the end of the list and will reload the menu
    // by passing the meta to the fetch function
    var extras = isFullTextSearch ? [ ] : [
      {
        text: 'Full user search...',
        meta: { fullTextSearch: true }
      }
    ];

    fetch(url).then(function(users) {
      // Where the user object must contain the properties `id` and `name`
      // but you could additionally include anything else you deem useful.
      success(users, extras);
    });
  }
});
```
