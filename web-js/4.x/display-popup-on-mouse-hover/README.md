# Display Popups on Mouse Hover

## About

This sample shows how to display popup upon mouse hover with ArcGIS API for JavaScript 4.x.

## How It Works

1. Set view.popup.autoOpenEnabled to false so that the popups do not open upon mouse click.

```javascript
      var view = new MapView({
        container: "viewDiv",
        map: map,
        center: [-95.7129, 37.0902],
        zoom: 5,
        popup: {
          autoOpenEnabled: false
        }
      });
```

2. Watch the view's "pointer-move" event and pass the event handler to a hitTest().

3. Call Popup.open() to open the popup.

```javascript
      view.on("pointer-move", function (event) {
        view.hitTest(event).then(function (response) {
          if (response.results.length) {
            var graphic = response.results.filter(function (result) {
              // check if the graphic belongs to the layer of interest
              return result.graphic.layer === featureLayer;
            })[0].graphic;
            view.popup.open({
              location: graphic.geometry.centroid,
              features: [graphic]
            });
          } else {
            view.popup.close();
          }
        });
      });
```


## Related Documentation

- [Popup.autoOpenEnabled](https://developers.arcgis.com/javascript/latest/api-reference/esri-widgets-Popup.html#autoOpenEnabled)
- [pointer-move event](https://developers.arcgis.com/javascript/latest/api-reference/esri-views-MapView.html#event-pointer-move)
- [MapView.hitTest()](https://developers.arcgis.com/javascript/latest/api-reference/esri-views-MapView.html#hitTest)

## [Live Sample](https://esri.github.io/developer-support/web-js/4.x/display-popup-on-mouse-hover/)
