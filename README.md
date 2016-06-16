
This fork provide the following on top of the original:

- The ability to provide custom HTTP headers in the options object (e.g Authorization)
- The module returns the actual EventSource implementation, rather than sometimes polyfilling, sometimes not.
- Typescript typings


How to use:
-------------------------

package.json
```
"event-source": "git://github.com/AlexGalays/EventSource.git"
```

```javascript
import EventSource from 'event-source'

const source = new EventSource('url', { headers: { Authorization: 'plz' } })
```


EventSource polyfill - http://www.w3.org/TR/eventsource/




Server-side requirements:
-------------------------

* "Last-Event-ID" is sent in a query string (CORS + "Last-Event-ID" header is not supported by all browsers)
* It is required to send 2 KB padding for IE < 10 and Chrome < 13 at the top of the response stream
* You need to send "comment" messages each 15-30 seconds, these messages will be used as heartbeat to detect disconnects - see https://bugzilla.mozilla.org/show_bug.cgi?id=444328

Build:
------

* To build EventSource, just install npm modules (`npm install`) and then run the build (`npm run build`). It should generate a new version of eventsource.min.js.

Notes:
-----
 * If you are using HTTP Basic Authentication, you can embed credentials into the URL - `http://username:password@github.com`.

Other EventSource polyfills:
----------------------------

* https://github.com/remy/polyfills/blob/master/EventSource.js by Remy Sharp
* https://github.com/rwldrn/jquery.eventsource by Rick Waldron
* https://github.com/amvtek/EventSource by AmvTek

License
-------
The MIT License (MIT)

Copyright (c) 2012 vic99999@yandex.ru

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
