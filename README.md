Utils library for JavaScript/TypeScript, so you don't have to reinvent the wheel.

## Installation
`$ npm i -s tlorc`

## Examples

```js
const tlorc = require('tlorc');
const TloEventWrapper = tlorc.TloEventWrapper;

const el = document.getElementById('foo');
const tloEvent = new TloEventWrapper(el);

function scrollEvent() {
  tloEvent.throttle('scroll', () => {
    // code here
  });
}
scrollEvent();
```
or
```js
import {TloEventWrapper} from 'tlorc';

const el = document.getElementById('foo');
const tloEvent = new TloEventWrapper(el);

function scrollEvent() {
  tloEvent.throttle('scroll', () => {
    // code here
  });
}
scrollEvent();
```

## Docs
#### TloEventWrapper
Used for managing DOM events.\
`new TloEventWrapper(element)`

| Method | Return Type |
| --- | --- |
| `add(types, callback)` | `void` |
| `throttle(types, callback, throttleTime = 100)` | `void` |
| `debounce(types, callback, debounceTime = 200)` | `void` |
| `remove(types)` | `void` |
| `removeAll()` | `void` |

The `types` parameter can be a string, an array of strings, an object `{type: string, useCapture?: boolean}` or 
an array of objects. The exception is the `remove` method, which only takes a string or an array of strings.
#### TloHttp
A fetch http client.\
`new TloHttp()`

| Method | Return Type |
| --- | --- |
| `get<ResponseBody>(url, options?)` | `Promise<ResponseBody>` |
| `get$Response<ResponseBody>(url, options?)` | `Promise<Response>` |
|  |  |
| `post<ResponseBody>(url, body, options?)` | `Promise<ResponseBody>` |
| `post$Response<ResponseBody>(url, body, options?)` | `Promise<Response>` |
|  |  |
| `put<ResponseBody>(url, body, options?)` | `Promise<ResponseBody>` |
| `put$Response<ResponseBody>(url, body, options?)` | `Promise<Response>` |
|  |  |
| `patch<ResponseBody>(url, body, options?)` | `Promise<ResponseBody>` |
| `patch$Response<ResponseBody>(url, body, options?)` | `Promise<Response>` |
|  |  |
| `delete<ResponseBody>(url, body, options?)` | `Promise<ResponseBody>` |
| `delete$Response<ResponseBody>(url, body, options?)` | `Promise<Response>` |

Methods with suffix $Response return the whole response object. Methods without the suffix only return the response body.

## Patch Notes
#### 1.1.2
- Fixed types for TloHttp body
- Improved the docs
#### 1.1.1
- Added TloHttp - a fetch http client (see docs for more details)
#### 1.0.1
- Fixed a bug with removing event listeners
- Fixed a bug with `new TloEventWrapper(element)` throwing an error for elements that may be null
#### 1.0.0
- Added `add` and `debounce` instance methods
- Changed the event handler's name from TloEvent to TloEventWrapper
- Added the option to set the `useCapture` parameter in TloEventWrapper methods
- Added the docs
- Fixed the callback reference
#### 0.2.3
- Fixed the main library path
#### 0.2.2
- Improved type checking
#### 0.2.0
- Added removing event listeners via `tloEvent.remove('eventName')` or `tloEvent.removeAll()`.
