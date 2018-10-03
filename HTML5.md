
## canvas

```html
<canvas id="canvas" style="border: 1px solid #000"></canvas>




<script>
    window.onload = function(){
            var canvas = document.getElementById('canvas');
            canvas.width = 1024;
            canvas.height = 768;
            var context = canvas.getContext('2d');

            context.beginPath();
            context.moveTo(100,100);
            context.lineTo(700,700);
            context.lineTo(100,700);
            context.lineTo(100,100);
            context.closePath();
            context.fillStyle = "rgba(0,0,0,0.6)";
            context.fill();

            context.lineWidth = 5;
            context.strokeStyle = "#005588";
            context.stroke();

            context.beginPath();
            context.moveTo(200,100);
            context.lineTo(700,600);
            context.closePath();
    }
</script>


```

### Web 存储

```js



```




