# node-apac - Node.js client for the Amazon Product Advertising API.

apac (Amazon Product Advertising Client) will allow you to access the Amazon Product Advertising API from Node.js. It supports the newly required Request Signatures which can be a bit tedious to generate on your own. [Learn more about the Amazon Product Advertising API](https://affiliate-program.amazon.com/gp/advertising/api/detail/main.html).

node-apac is just a thin wrapper around Amazon's API. The only intent is to take care of request signatures, performing the HTTP requests, processing the responses and parsing the XML. You should be able to run any operation becuase the operation and all parameters are passed directly to the execute method just as they will be passed to Amazon. The result is that you feel likely you're working directly with the API, but you don't have to worry about some of the more teadious tasks.

_**Important**: I am not able to devote time to maintain this code properly. If anyone is interested in taking over that responsibility, please let me know._

## Installation

Install using npm:
```bash
$ npm install apac@latest
```

If you try to install without "@latest", it will try to install the most recent stable
version, but there is no stable version yet. So for now you must specify latest.

## Quick Start

Here is a quick start to help you get node, npm and node-apac installed and running:
[node-apac Quick Start](http://www.synchrosinteractive.com/blog/1-software/39-node-apac-quick-start)

Here's a quick example:
```javascript
var util = require('util'),
    OperationHelper = require('apac').OperationHelper;

var opHelper = new OperationHelper({
    awsId:     '[YOUR AWS ID HERE]',
    awsSecret: '[YOUR AWS SECRET HERE]',
    assocId:   '[YOUR ASSOCIATE TAG HERE]'
});

opHelper.execute('ItemSearch', {
    'SearchIndex': 'Books',
    'Keywords': 'harry potter',
    'ResponseGroup': 'ItemAttributes,Offers'
}, function(error, results) {
    if (error) { console.log('Error: ' + error + "\n") }
    console.log("Results:\n" + util.inspect(results) + "\n");
});
```

Results are returned as a JSON object (XML results parsed using xml2js -- thanks pierrel).

## API Documentation

Because we don't define any specific operations, we also don't document them. What a waste
when you can find them all here:
[API Reference](http://docs.amazonwebservices.com/AWSECommerceService/latest/DG/index.html?ProgrammingGuide.html)

## License

Copyright (c) 2010 Dustin McQuay. All rights reserved.

Permission is hereby granted, free of charge, to any person
obtaining a copy of this software and associated documentation
files (the "Software"), to deal in the Software without
restriction, including without limitation the rights to use,
copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the
Software is furnished to do so, subject to the following
conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.
