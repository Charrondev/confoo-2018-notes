# Workers of the World, Unite!

A talk about web workers, not workers unions.

## WebWorkers for Speed

Websites should aim for 60fps. Cannot do much for each frame. _16ms per frame._

In JS a page runs in a single thread. Everything competes for 1/60th of a frame. JS can block the main thread. A single thread cannot compute and paint.

- Webworkers allow an extra thread for JS to compute on.
- Webworkers can only be server from a server

```js
const worker = new Worker("worker.js")
worker.onmessage = function (e) {
    renderPrimes(e.data);
}
work.postMessage({
    cmd: 'primes', n // Large serialization overhead here.
});

// worker.js
onmessage = fucntion (e) {
    // ...compute things here
    self.postMessage()
}
```

- Possible to pass a Buffer without serialization. But you can never mutate that object again.
- Normal JS optimization methods are applicable to Workers as well.
  - Always measure before total time
  - `navigator.hardwareConcurrency` to determine how many threads you can spawn.

### Example

https://glebbahmutov.com/blog/fast-legoization

### Libraries

Create web workers on the fly asynchronously. Cannot use items from external context from the closure.

- GreenLet
- worker-loader for webpack.

### Support 

IE11+ support.

### What can webworkers do

- JS
- JSON
- IndexedDB
- AJAX
- …but not DOM
- VirtualDOM

### Resources

Feather App - https://github.com/HenrikJoreteg/feather-app

- Minimal implementation

## ServiceWorker

Blurring the line between client and server. 

- Has it's own thread. 
- Multiple browser threads share the same ServiceWorker.
- Can intercept and transform requests/responses through Ajax.
- The browser doesn't know the difference between talking to the ServiceWorker or the server.
- Functions as a proxy between the browser and the server.
- Every browser than supports ServiceWorker supports async/await.
- Does not require a PWA.

**browser**

- window 
- localstorage
- XMLHttpRequest/fetch
- document

**webworker**

- self


- IndexDB, Cache API


- XMLHttpRequest/fetch

**Service worker**

- self


- IndexDB, Cache API


- fetch

### Events

- `install`


- `activate`
- `message`
- `push`
- `fetch`

### Use Cases

- Cache resources on `install` (tell browser to cache a bunch of resources not necessarily in the page).
- Listen on `fetch` to return things from the Cache API. No need to actually make a network request at all.

### Caching stategies

https://developers.google.com/web/tools/workbox

- Cache only.
- Cache with network fallback.
- Cache then netwrok fresfresh.
- Network only.
- Network with cache fallback.

### Over the top

Run the same server side code in a service worker (EG. Node.js/express server).

https://github.com/bahmutov/express-service

### Support

Almost there!!! All previews of major browser contain ServiceWorkers.

### Next / Nuxt / Sapper

All server side js libraries that implement service workers for preloading.

https://serviceworke.rs/cache-from-zip.html

### What if an attacker can load a malicious ServiceWorker script?

- Be very carefull of XSS attacks.
- Malicious ServiceWorker injected via XSS can be really hard to get rid of.
- https://glebbahmutov.com/blog/disable-inline-javascript-for-security