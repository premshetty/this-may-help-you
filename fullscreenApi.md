# api to request full screen


```js
 const viewFullScreen = (id) => {
    let elem = document.getElementById(id);
    if (!document.fullscreenElement) {
      elem.requestFullscreen().catch((err) => {
        alert(
          `Error attempting to enable fullscreen mode: ${err.message} (${err.name})`
        );
      });
    } else {
      document.exitFullscreen();
    }
  };
```
