### `advlist_number_styles`

This option allows you to include specific ordered list item markers in the default `numlist` toolbar control.

**Type:** `String`

**Default Value:** `'default,lower-alpha,lower-greek,lower-roman,upper-alpha,upper-roman'`

**Possible Values:**

  * `default`: your browser's default style
  * `lower-alpha`: lowercase ASCII letters, e.g. a, b, c, ... z
  * `lower-greek`: lowercase classical Greek (alpha, beta, gamma), e.g. α, β, γ ...
  * `lower-roman`: lowercase roman numerals, e.g. i, ii, iii, iv, v ...
  * `upper-alpha`: uppercase ASCII letters, e.g. A, B, C, ... Z
  * `upper-roman`: uppercase roman numerals, e.g. I, II, III, IV, V ...

#### Example: Using `advlist_number_styles`

```js
tinymce.init({
  selector: 'textarea',  // change this value according to your HTML
  plugins: 'advlist',
  advlist_number_styles: 'lower-alpha'  // only include lower alpha in list
});
```