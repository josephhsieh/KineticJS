To create a ellipse with `KineticJS`, we can instantiate a `Kinetic.Ellipse()` object.  For a full list of attributes and methods, check out the [Kinetic.Ellipse documentation](http://kineticjs.com/docs/Kinetic.Ellipse.html).

<iframe width="350" height="350" src="../Examples/Shapes/Ellipse.html" frameborder="0" allowfullscreen></iframe>

```html
<!DOCTYPE HTML>
<html>
  <head>
    <style>
      body {
        margin: 0px;
        padding: 0px;
      }
    </style>
  </head>
  <body>
    <div id="container"></div>
    <script src="http://d3lp1msu2r81bx.cloudfront.net/kjs/js/lib/kinetic-v5.1.0.min.js"></script>
    <script defer="defer">
      var stage = new Kinetic.Stage({
        container: 'container',
        width: 300,
        height: 300
      });

      var layer = new Kinetic.Layer();

      var oval = new Kinetic.Ellipse({
        x: stage.getWidth() / 2,
        y: stage.getHeight() / 2,
        radius: {
          x: 100,
          y: 50
        },
        fill: 'yellow',
        stroke: 'black',
        strokeWidth: 4
      });

      // add the shape to the layer
      layer.add(oval);

      // add the layer to the stage
      stage.add(layer);
    </script>
  </body>
</html>

```