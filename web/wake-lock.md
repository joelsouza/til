# Screen Wake Lock API

Screen Wake Lock API provides a way to prevent devices from dimming or locking the screen when an application needs to keep running.

There are plenty of use cases for keeping a screen on, including reading an ebook, map navigation, following a recipe, scanning a QR/barcode or applications that use voice or gesture control, rather than tactile input (the default way to keep a screen awake).

## Feature Detection

```javascript
if ('wakeLock' in navigator) {
  isSupported = true;
  statusElem.textContent = 'Screen Wake Lock API supported!';
} else {
  wakeButton.disabled = true;
  statusElem.textContent = 'Wake lock is not supported by this browser.';
}
```

## Demo

```javascript
// Create a reference for the Wake Lock.
let wakeLock = null;

// create an async function to request a wake lock
try {
  wakeLock = await navigator.wakeLock.request('screen');
  statusElem.textContent = 'Wake Lock is active!';
} catch (err) {
  // The Wake Lock request has failed - usually system related, such as battery.
  statusElem.textContent = `${err.name}, ${err.message}`;
}
```

## "Releasing" a wake lock

```javascript
wakeLock.release()
  .then(() => {
    wakeLock = null;
  });
```

### Listening for wake lock release

The `sentinel` is attached to the underlying system wake lock. It can be `released` by the system if the battery power is too low or the document is not active or visible. It can also be released manually via the `WakeLockSentinel.release()` method. It is good practice to store a reference to the sentinel object to control release later and also to reacquire the lock if need be.

```javascript
wakeLock.addEventListener('release', () => {
  // the wake lock has been released
  statusElem.textContent = 'Wake Lock has been released';
});
```

## Reacquiring a wake lock

```javascript
document.addEventListener('visibilitychange', async () => {
  if (wakeLock !== null && document.visibilityState === 'visible') {
    wakeLock = await navigator.wakeLock.request('screen');
  }
});
```