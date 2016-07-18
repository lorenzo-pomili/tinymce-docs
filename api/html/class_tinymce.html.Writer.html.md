---
layout: default
title: tinymce.html.Writer
---

|  |  |
| --- | --- |
| Namespace | tinymce.html |
| Class | Writer |

This class is used to write HTML tags out it can be used with the Serializer or the SaxParser.<span>Version:</span>3.4      

**Example**  

## Public Methods

| Method | Defined By |
| --- | --- |
| [Writer](#writer)(settings:Object) : Constructs a new Writer instance. | Writer |
| [cdata](#cdata)(text:String):void : Writes a cdata node such as . | Writer |
| [cdata](#cdata)(text:String):void : Writes a comment node such as . | Writer |
| [doctype](#doctype)(text:String):void : Writes a doctype node such as . | Writer |
| [end](#end)(name:String):void : Writes the a end element such as . | Writer |
| [getContent](#getcontent)():String : Returns the contents that got serialized. | Writer |
| [pi](#pi)(name:String, text:String):void : Writes a PI node such as . | Writer |
| [reset](#reset)():void : Resets the internal buffer if one wants to reuse the writer. | Writer |
| [start](#start)(name:String, attrs:Array, empty:Boolean):void : Writes the a start element such as . | Writer |
| [text](#text)(text:String, raw:Boolean):void : Writes a text node. | Writer |

## Method details

### Writer 

***public function Writer(settings:Object)***  
Constructs a new Writer instance.      

**Parameters**  

| Param | Detail |
| --- | --- |
| settings:Object | Name/value settings object. |

### cdata 

***public function cdata(text:String):void***  
Writes a cdata node such as .      

**Parameters**  

| Param | Detail |
| --- | --- |
| text:String | String to write out inside the cdata. |

### cdata 

***public function cdata(text:String):void***  
Writes a comment node such as .      

**Parameters**  

| Param | Detail |
| --- | --- |
| text:String | String to write out inside the comment. |

### doctype 

***public function doctype(text:String):void***  
Writes a doctype node such as .      

**Parameters**  

| Param | Detail |
| --- | --- |
| text:String | String to write out inside the doctype. |

### end 

***public function end(name:String):void***  
Writes the a end element such as.      

**Parameters**  

| Param | Detail |
| --- | --- |
| name:String | Name of the element. |

### getContent 

***public function getContent():String***  
Returns the contents that got serialized.      

**Returns**  
String - HTML contents that got written down.

### pi 

***public function pi(name:String, text:String):void***  
Writes a PI node such as .      

**Parameters**  

| Param | Detail |
| --- | --- |
| name:String | Name of the pi. |
| text:String | String to write out inside the pi. |

### reset 

***public function reset():void***  
Resets the internal buffer if one wants to reuse the writer.

### start 

***public function start(name:String, attrs:Array, empty:Boolean):void***  
Writes the a start element such as

.

**Parameters**  

| Param | Detail |
| --- | --- |
| name:String | Name of the element. |
| attrs:Array | Optional attribute array or undefined if it hasn't any. |
| empty:Boolean | Optional empty state if the tag should end like <br />. |

### text 

***public function text(text:String, raw:Boolean):void***  
Writes a text node.      

**Parameters**  

| Param | Detail |
| --- | --- |
| text:String | String to write out. |
| raw:Boolean | Optional raw state if true the contents wont get encoded. |