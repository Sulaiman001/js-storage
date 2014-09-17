# JsStorage

######A Very Simple Browser Storage Abstraction

js-storage.js is a pretty dumbed-down browser storage abstraction. If the browser supports localStorage, it stores data in localStorage. If not, it stores it into the cookies (up to a max of 4093 bytes in browser cookies). It's meant for storing small amounts of settings on web pages (I use it for SPA's that require user setting persistency).

Emptying the storage or unsetting specific keys through JsStorage's unset() and empty() won't effect the rest of the localStorage keys or cookies stored at the current domain. Everything is converted to and from JSON and stored into one unique key (or cookie).

JsStorage supports storing objects and arrays as well as strings, integers, etc.

###Setup

`<script src="js/js-storage.min.ks"></script>`  

###Usage
```
JsStorage.get('name'); // returns: undefined

JsStorage.set('name', 'Nebez');
JsStorage.get('name'); // returns: 'Nebez'

var myObject = {
    foo: 'bar',
    something: 'cool',
    js: 'storage'
};
JsStorage.set('myObject', myObject);
JsStorage.get('myObject'); // returns: Object { foo: 'bar', something: 'cool', js: 'storage' }

JsStorage.unset('name');
JsStorage.get('name'); // returns: undefined

JsStorage.set('foo', 'bar');
JsStorage.empty();
JsStorage.get('foo'); // returns: undefined
```