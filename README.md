html2js-bin
===========

A node-based command-line HTML inlining tool.

```
npm install html2js-bin
```

Usage
-----

```
html2js [options] <input-file>
```

In no input file is specified, `html2js` will read from stdin.

### Options

* **output**: Optional output file, default to stdout
* **template**: A template file for wrapping the output
* **pattern**: A pattern to replace in the template file

You can run `html2js --help` for a full listing of options.


### Example

Given `index.html`

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Hello World</title>
  </head>
  <body>
    <h1>Hello World</h1>
    <p>Hello World</p>
  </body>
</html>
```

Running

```
html2js index.html
```

Output:

```javascript
'<!DOCTYPE html>\n' +
'<html>\n' +
'  <head>\n' +
'    <title>Hello World</title>\n' +
'  </head>\n' +
'  <body>\n' +
'    <h1>Hello World</h1>\n' +
'    <p>Hello World</p>\n' +
'  </body>\n' +
'</html>'
```


### Template Example

Given `template.js`

```javascript
define(function() {
    return <!-- HTML -->
});
```

Running

```
html2js -t template.js -p '<!-- HTML -->' index.html
```

Output:

```javascript
define(function() {
    return '<!DOCTYPE html>\n' +
'<html>\n' +
'  <head>\n' +
'    <title>Hello World</title>\n' +
'  </head>\n' +
'  <body>\n' +
'    <h1>Hello World</h1>\n' +
'    <p>Hello World</p>\n' +
'  </body>\n' +
'</html>'
});
```


Contributing
------------

Contributions of bug reports, feature requests, and pull requests are greatly appreciated!

Please note that this project is released with a [Contributor Code of Conduct](https://github.com/dpogue/skytrain-service-map/blob/master/CODE_OF_CONDUCT.md). By participating in this project you agree to abide by its terms.


Licence
-------

Copyright © 2016 Darryl Pogue
Licensed under the MIT Licence.
