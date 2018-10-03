
## canvas

```html
<canvas id="canvas" style="border: 1px solid #000"></canvas>




<script>
    window.onload = function(){
        var canvas = document.getElementById('canvas');
        canvas.width = 1024;
        canvas.height = 768;
        var content = canvas.getContext('2d');
    }
</script>


```


