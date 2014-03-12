# Libxmljs
[![Build Status](https://secure.travis-ci.org/polotek/libxmljs.png?branch=master)](http://travis-ci.org/polotek/libxmljs)

LibXML bindings for [node.js](http://nodejs.org/)

```javascript
var libxmljs = require("libxmljs");
var xml =  '<?xml version="1.0" encoding="UTF-8"?>' +
           '<root>' +
               '<child foo="bar">' +
                   '<grandchild baz="fizbuzz">grandchild content</grandchild>' +
               '</child>' +
               '<sibling>with content!</sibling>' +
           '</root>';

var xmlDoc = libxmljs.parseXml(xml);

// xpath queries
var gchild = xmlDoc.get('//grandchild');

console.log(gchild.text());  // prints "grandchild content"

var children = xmlDoc.root().childNodes();
var child = children[0];

console.log(child.attr('foo').value()); // prints "bar"
```

Example 2 conditional grandchild value at attribute
```javascript
#!/usr/local/bin/node

var libxmljs = require("libxmljs");
var xml =  '<?xml version="1.0" encoding="UTF-8"?>' +
           '<root>' +
               '<child foo="bar">' +
                   '<grandchild baz="fizbuzz">grandchild content</grandchild>' +
                   '<grandchild baz="fiz">grandchild content 2</grandchild>' +
                   '<grandchild baz="buzz" faz="3">grandchild content 3</grandchild>' +
               '</child>' +
               '<sibling>with content!</sibling>' +
           '</root>';

var xmlDoc = libxmljs.parseXml(xml);

var specificgchild = xmlDoc.get('/root/child/grandchild[@baz="buzz"]');
console.log( specificgchild.text() );
console.log( specificgchild.attr('faz').value() );
```


## Support

* Docs - [http://github.com/polotek/libxmljs/wiki](http://github.com/polotek/libxmljs/wiki)
* Mailing list - [http://groups.google.com/group/libxmljs](http://groups.google.com/group/libxmljs)

## API and Examples

Check out the wiki [http://github.com/polotek/libxmljs/wiki](http://github.com/polotek/libxmljs/wiki).

See the [examples](https://github.com/polotek/libxmljs/tree/master/examples) folder.

## Installation via [npm](https://npmjs.org)

```shell
npm install libxmljs
```

## Contribute

Start by checking out the [open issues](https://github.com/polotek/libxmljs/issues?labels=&page=1&state=open). Specifically the [desired feature](https://github.com/polotek/libxmljs/issues?labels=desired+feature&page=1&state=open) ones.

### Requirements

Make sure you have met the requirements for [node-gyp](https://github.com/TooTallNate/node-gyp#installation). You DO NOT need to manually install node-gyp; it comes bundled with node.

