# Cross Platform Progressive Web Apps

_Simon MacDonald_ **@macdonst**

## What is a Progressive Web App

> Progressive Web Apps use modern web capabilities to deliver an app-liek user experience
>
> They evolve from pages in browser tabs to immersive, top-level apps.

PWA's are really just web pages. Not all pieces of functionaility needs to be available to considered a PWA. Pieces can be added progressively over time.

### Why

Offline/Low connectivity web pages.

### What

**Progressive**

Works for every user regardless of browser choice because it's built with progressive enhancement as a core tenet.

**Responsive**

Fits and form factor: desktop, mobile, tablet, or whatever is next.

**Connectivity Independent**

Enhanced with service workers to work offline or on low-quality networks. Not all functionaility needs to be available offline.

**App Like**

Feels like an app, because the app shell model seperates the application functionality from the application content. The App Shell should definitely be cached. Older content should be cached as well.

**Safe**

Served via HTTPS to prevent snooping and to ensure content hasn't been tampered. Service Workers only work via HTTPS or on localhost. Web Share + GeoLocation APIs are HTTPS only.

**Re-engagable**

Makes re-engagement easy through features like push notifications. If you are going to need to use notifications, don't prompt the client immediately. Explain to the user first, why you need these permissions.

**Installable**

Allows users to add apps they find most useful to their home screen without the hassle of an app store (Web App Manifest).

**Linkable**

Easily share the application via URL, does not require complex installation.

**Discoverable**

```html
<link rel="manifest" src="manifest.json">
```

```json
{
    "short_name": "PWA Test",
    "name": "Longer Full PWA Test name",
    "start_url": "index.html?start='addedToHomeScreen'",
    "display": "standalone|fullscreen|minimalui",
    "background_color": "#FFF",
    "theme_color": "#333",
    "derscription": "Some description",
    "icons":{...}
}
```

## Compatibility

Chrome, IE, Firefox



**Apple/Safari** :😢

- Coming in iOS 11.3 (beta 3 now).

**Broken things**

- Input type fole
- Breaks integration with camera
- No support for getUserMedia

Right now it's best not to use native PWAs on iOS due to inconsistencies and bugs in iOS 10, 11, and 11.3. Recomendation if you need the app on iOS: Cordova/PhoneGap with the PWA plugin.





