To create an sprite with `KineticJS`, we can instantiate a `Kinetic.Sprite()` object.  For a full list of attributes and methods, check out the [Kinetic.Sprite documentation](http://kineticjs.com/docs/Kinetic.Sprite.html).

<iframe width="650" height="350" src="../Examples/Shapes/Sprite.html" frameborder="0" allowfullscreen></iframe>

```html
<!DOCTYPE HTML>
<html>
  <head>
    <style>
      body {
        margin: 0px;
        padding: 0px;
      }
      #container {
        background-color: #222;
        display: inline-block;
        width: 580px;
        height: 202px;
      }
      #buttons {
        position: absolute;
        top: 5px;
        left: 10px;
        z-index: 4;
      }
      #buttons > input {
        padding: 10px;
        display: block;
        margin-top: 5px;
      }
    </style>
  </head>
  <body>
    <div id="buttons">
      <input type="button" id="punch" value="Punch">
    </div>
    <div id="container"></div>
    <script src="http://d3lp1msu2r81bx.cloudfront.net/kjs/js/lib/kinetic-v5.1.0.min.js"></script>
    <script defer="defer">
      var stage = new Kinetic.Stage({
        container: 'container',
        width: 578,
        height: 200
      });
      var layer = new Kinetic.Layer();
      var animations = {
        idle: [
          2, 2, 70, 119,
          71, 2, 74, 119,
          146, 2, 81, 119,
          226, 2, 76, 119
        ],
        punch: [
          2, 138, 74, 122,
          76, 138, 84, 122,
          346, 138, 120, 122
        ]
      };

      var imageObj = new Image();
      imageObj.onload = function() {
        var blob = new Kinetic.Sprite({
          x: 250,
          y: 40,
          image: imageObj,
          animation: 'idle',
          animations: animations,
          frameRate: 7,
          frameIndex: 0
        });

        // add the shape to the layer
        layer.add(blob);

        // add the layer to the stage
        stage.add(layer);


        // start sprite animation
        blob.start();

        // resume transition
        document.getElementById('punch').addEventListener('click', function() {
          blob.setAnimation('punch');
          blob.on('frameIndexChange.button', function() {
            if (this.frameIndex() === 2) {
              setTimeout(function() {
                blob.setAnimation('idle');
                blob.off('.button');
              }, 1000 / blob.frameRate());
              
            }
          })
        }, false);
      };
      imageObj.src = '../../img/blob-sprite.png';
    </script>
  </body>
</html>
```