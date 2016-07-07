---
layout: default
title: JSP
---

TinyMCE Compressor gzips all JavaScript files in TinyMCE into a single streamable file. This makes the overall download size 75% smaller, and the number of requests will also be reduced. The overall initialization time for TinyMCE will be reduced dramatically if you use this script.

## Installation

Here is a step by step list on how to install the GZip compressor.

1.  Copy the tiny_mce_gzip.js and tiny_mce_gzip.jsp to the tiny_mce directory (i.e., the same directory that contains the tiny_mce.js file).
2.  Remove the current script tag. <script type="text/javascript" src="tinymce/jscripts/tiny_mce/tiny_mce.js"></script>
3.  Add the new new GZip script <script type="text/javascript" src="tinymce/jscripts/tiny_mce/tiny_mce_gzip.js"></script>.
4.  Add the new GZip initialization call that will tell the compressor what to include in the output. This should be the sum of all the themes and plugins required by the implementation.

## Example of initialization

The example below will pack both themes and all plugins into one file/stream. Remove the things you don't need or add your custom plugins to the settings below. Remember that the tinyMCE_GZ.init call must be placed in its own script tag.

```html
<script type="text/javascript" src="tinymce/jscripts/tiny_mce/tiny_mce_gzip.js"></script>
<script type="text/javascript">
tinyMCE_GZ.init({
	plugins : 'style,layer,table,save,advhr,advimage,advlink,emotions,iespell,insertdatetime,preview,media,searchreplace,print,contextmenu',
	themes : 'simple,advanced',
	languages : 'en',
	disk_cache : true,
	debug : false
});
</script>
<script type="text/javascript">
tinyMCE.init({
	.. your normal init ..
});
</script>

```

## Troubleshooting

*   The GZip compressor can fail to load if the server has odd settings or is missing the required support for it to function. To see compilation errors or other problems we suggest that you use HTTP debugging tools like [Fiddler](http://www.fiddlertool.com/fiddler/) or [Firebug](http://www.getfirebug.com/) you can also point you browser directly to the GZip file.
*   Consult the changelog of this script and make sure that you use the latest version of TinyMCE. These two parts are pretty much tied together so there is no guarantee that it will work with older versions of TinyMCE.
*   Visit the [TinyMCE forum](http://tinymce.moxiecode.com/forum) for help with the TinyMCE Gzip Compressor.
*   To remove a plugin, remember to remove it both from tinyMCE_GZ.init and TinyMCE.init.
*   To add a plugin, remember to add it both to the tinyMCE_GZ.init and the tinyMCE.init calls.
*   A patched version of 1.0.4 adjusted for a common error with JSP paths and output is at [sourceforge](http://sourceforge.net/tracker/index.php?func=detail&aid=1623519&group_id=103281&atid=635682).