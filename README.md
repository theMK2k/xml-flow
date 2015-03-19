# xml-flow
##### An XML/HTML stream reader, now with less suck!

Dealing with XML data can be frustrating. Especially if you have a whole-lot of it. Most XML readers work on the entire XML document as a String: this can be problematic if you need to read very large XML files. With xml-flow, you can use streams to only load a small part of an XML document into memory at a time.

xml-flow has only one dependency, [sax-js](https://github.com/isaacs/sax-js). This means it will run nicely on windows environments.

## Installation

```
$ npm install xml-flow
```

## Getting started
xml-flow tries to keep the parsed output as simple as possible. Here's an example:

### Input File
```xml
<root>
  <person>
    <name>Bill</name>
    <id>1</id>
    <age>27</age>
  </person>
  <person>
    <name>Sally</name>
    <id>2</id>
    <age>29</age>
  </person>
  <person>
    <name>Kelly</name>
    <id>3</id>
    <age>37</age>
  </person>
</root>
```

### Usage
```js
var fs = require('fs')
  , flow = require('xml-flow')
  , inFile = fs.createReadStream('./your-xml-file.xml')
  , xmlStream = flow(inFile)
;

xmlStream.on('tag:person', function(person) {
  console.log(person);
});

```
### Output
```
{name: 'Bill', id: '1', age: '27'}
{name: 'Sally', id: '2', age: '29'}
{name: 'Kelly', id: '3', age: '37'}
```

## Authors

  - [Matthew Larson](https://github.com/matthewmatician)

# License

  MIT

[npm-url]: https://npmjs.org/package/xml-flow
