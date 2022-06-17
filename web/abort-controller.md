# AbortController

The `AbortController` interface represents a controller object that allows you to abort one or more Web requests as and when desired.

You can create a new `AbortController` object using the `AbortController()` constructor. Communicating with a DOM request is done using an `AbortSignal` object.

```html
<button id="download" data-file="path/to/the-file.mp4">download</button>
<button id="cancel">cancel</button>
```

```javascript
  let controller;
  const downloadBtn = document.getElementById('#download');
  const abortBtn = document.getElementById('#abort');

  downloadBtn.addEventListener('click', fetchVideo);

  abortBtn.addEventListener('click', function() {
    if (controller) controller.abort();
    console.log('Download aborted');
  });

  function fetchVideo() {
    controller = new AbortController();
    const signal = controller.signal;
    const url = downloadBtn.dataset.file
    fetch(url, { signal })
      .then(function(response) {
        console.log('Download complete', response);
      })
      .catch(function(e) {
        console.log('Download error: ' + e.message);
      });
  }
```
