# google-transparency.js
A Google Maps plugin that allows to add an opacity control.

_For a working example (without API Key) see [demo](https://raruto.github.io/examples/google-transparency/google-transparency.html)_

---

> _Initally based on the [work](http://www.gavinharriss.com/code/opacity-control) of **Gavin Harriss**_

---

## How to use

1. **include CSS & JavaScript**
    ```html
    <head>
    ...
    <style>html, body, #map { width: 100%; height: 100%; margin: 0; padding: 0; }</style>
    <script src="https://maps.google.com/maps/api/js?key=<INSERT_HERE_API_KEY>"></script>
    <script src="https://raruto.github.io/cdn/google-transparency/0.0.1/google-transparency.js"></script>
    ...
    </head>
    ```
2. **choose the div container used for the slippy map**
    ```html
    <body>
    ...
    <div id="map"></div>
    ...
    </body>
    ```
3. **create your first simple “google-transparency” slippy map**
    ```html
    <script>
      var mapOpts = {
        center: new google.maps.LatLng(-42.8598, 171.8043),
        zoom: 13,
        mapTypeId: google.maps.MapTypeId.SATELLITE,
      }

      var map = new google.maps.Map(document.getElementById('map'), mapOpts);

      var image_overlay = new OpacityControl(map, {
        opacity: 100,
        getTileUrl: function(coord, zoom) {
          // Restricting tiles to the small tile set we have in the example
          if (zoom == 13 && coord.x >= 8004 && coord.x <= 8006 && coord.y >= 3013 && coord.y <= 3015) {
            return "http://www.gavinharriss.com/codefiles/opacity-control/tiles/" + zoom + "-" + coord.x + "-" + coord.y + ".png";
          } else {
            return "http://www.gavinharriss.com/codefiles/opacity-control/tiles/blanktile.png";
          }
        },
      });

      var basemap_overlay = new OpacityControl(map, {
        opacity: 0.1,
        sliderImageUrl: "https://raruto.github.io/cdn/google-transparency/0.0.1/opacity-slider2.png",
        backgroundColor: "rgba(229, 227, 223, 0.9)",
        position: google.maps.ControlPosition.RIGHT_TOP
      }, );
    </script>
    ```
---

**Compatibile with:** gmaps@3.34

---

**Contributors:** [GavinHarriss](https://github.com/gavinharriss/google-maps-v3-opacity-control/), [Klokan](https://www.maptiler.com/blog/2008/11/opacity-control-for-google-maps-in.html), [Raruto](https://github.com/Raruto/google-transparency)
