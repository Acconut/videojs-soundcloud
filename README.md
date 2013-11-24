videojs-soundcloud
==================

A [videojs/video-js](https://github.com/videojs/video.js) plugin to support soundcloud links e.g [https://soundcloud.com/vaughan-1-1/this-is-what-crazy-looks-like](https://soundcloud.com/vaughan-1-1/this-is-what-crazy-looks-like)


How to use
==============================
```html
<head>
  <!-- Mandatory videojs include! -->
  <script src="http://vjs.zencdn.net/4.2.2/video.js"></script>
  <link href="http://vjs.zencdn.net/4.2.2/video-js.css" rel="stylesheet">
  <script src="../src/media.soundcloud.js"></script>
</head>
<body>
  <video
    id="myStuff"
    class="video-js vjs-default-skin"
    controls
    preload="auto"
    width="100%"
    height="360"
    data-setup=''
    ></video>
    
    <script>
      videojs("myStuff", {
        techOrder: ["soundcloud"],
        src: "https://soundcloud.com/vaughan-1-1/this-is-what-crazy-looks-like"
      });
    </script>
</body>
```


How it works
============
We create an iframe (with a soundcloud-embed URL) in the player-element and, using the soundcloud [Widget API](http://developers.soundcloud.com/docs/api/html5-widget) we initialize a widget that will give us the control methods, getters and setters we need.

More in detail notes
--------------------
> [**Getters**](http://developers.soundcloud.com/docs/api/html5-widget#methods)

> Since communication between the parent page and the widget's iframe is implemented through [window.postMessage](https://developer.mozilla.org/en/DOM/window.postMessage), it's not possible to return the value synchronously. Because of this, every getter method accepts a callback function as a parameter which, when called, will be given the return value of the getter method.

Due to this we have quite a few state variables when using the widget API.
