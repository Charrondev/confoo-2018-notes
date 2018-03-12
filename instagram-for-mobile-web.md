# Why and How Instagram Built for Mobile Web

_Jenny Lin_, Engineering Manager, Instagram Web

**Mobile web** allows connection among more people with limited devices and network connections.

## Why didn't people want the native app

- People with low connectivity had trouble downloading the app at all (too slow)
- Not enough device storage.

## Bringing filters to the web

- Use WebGL (direct port from the app's OpenGL).
- Launched an A/B test with the filters and found metrics down.
- Performance was too slow.
- Fixed performance by:
  - Profiling.
  - Lazy loading.

## Progressive Web App

- Service Workers (Workbox is a library to abstract away service workers).
- Web App Manifest (add to home screen, full-screen mode) chrome flag to bypass engagement check for PWAs.
- Takes up less storage than native app (and battery usage is blamed on the browser, not your app for now).
- Android only for now. Coming to iOS in 11.3
- Custom prompt for add to home screen: Listen for homescreen prompt when you set up, prevent default, and save the event to refire it.
- Offline mode (listen for offline event, but it is an unreliable event, need to fire off a tiny get request to actually know if they're online or not inside the event listener).
  - Save the request in IndexDB/service worker.
- Notifications
- Performance (with service workers)
  - Preload navigation.
  - Special caching mechanisms.

## Bundle Splitting

Split items that

- Able to cache longer.
- Able to opportunisticly load.
- Vendor libraries.
- Routes - components needed to render a given client side route.
  - Some routes share common modules, so these were pulled out into a common module.
- Webpack runtime (small bundle for async loading. Changes constantly with hashes to other bundles. Inlined into HTML).
- Non-critical path UI.

## Javascript bytecode caching

- Storing javascript bytecode into the network cache. Stored with the sourcecode as alternate content. 
- Provides smaller ~10% load performance.

## Embeds

Allow the site's own content to be embedded in other places.

Ways to claim users through embeds:

1. Get yourself embedded more.
2. Make users more likely to click the embed.
   1. Use Shadow DOM instead of iFrame. Important to remove use information/signed in info from the embed.
3. Make it easier for users to sign/in register when they come through from the embed.

## SEO

- Fixed issues.
- Add site directories in the footer for SEO.

## How do you determine which devices get served what version

By user agent.