# Logger

> HTTP request logger middleware for [luvit.io](http://luvit.io) and [Utopia](https://github.com/luvitrocks/luvit-utopia) server framework.

## Install

```bash
lit install voronianski/logger
```

## API

### ``logger(format, options)``

Create logger middleware function using the given ``format`` string and ``options`` table. Format argument is a predefined name string ([see below for the names](https://github.com/luvitrocks/luvit-logger#predefined-formats)).

### Options

- ``stream`` - output stream for writing log lines, defaults to ``process.stdout``.
- ``immediate`` - write log line on request instead of response, it means that a requests will be logged even if the server crashes, but data from the response cannot be logged (like the response code), defaults to ``false``.

### Predefined formats

For now there are three formats provided

##### default

```
:date :method :url HTTP/:http-version :status :res[content-length] - :response-time ms :user-agent
```

##### dev

```
:method :url :status :response-time ms - :res[content-length]
```

##### short

```
:date - :method :url HTTP/:http-version :status :res[content-length] - :response-time ms
```

## Example

```lua
local Utopia = require('utopia')
local logger = require('logger')

local app = Utopia:new()

app:use(logger('dev'))

app:listen(8080)
```

## License

MIT Licensed

Copyright (c) 2014-2016 Dmitri Voronianski [dmitri.voronianski@gmail.com](mailto:dmitri.voronianski@gmail.com)

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
