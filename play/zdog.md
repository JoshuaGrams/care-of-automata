---
title: Zdog
description: Round, flat, designer-friendly pseudo-3D engine.
---

<style>
.dragRotateCanvas {
	background-color: #fdb;
	cursor: move;
}
</style>

<script src="https://unpkg.com/zdog@1/dist/zdog.dist.min.js"></script>

<canvas id="my-demo" width="240" height="240" class="dragRotateCanvas"></canvas>

<script>
let isSpinning = true

let illo = new Zdog.Illustration({
	element: '#my-demo',
	dragRotate: true,
	onDragStart: function() { isSpinning = false },
	onDragEnd: function() {
		// Start spinning again after 1.5 seconds.
		setTimeout(function() { isSpinning = true }, 1.5 * 1000)
	}
})

function animate() {
	if(isSpinning) illo.rotate.y += 0.03
	illo.updateRenderGraph()
	requestAnimationFrame(animate)  // animate again on next redraw
}

animate()


// Add shapes to the illustration.

let purpleCircle = new Zdog.Ellipse({
	addTo: illo,
	diameter: 80,
	translate: { z: 40 },
	stroke: 20,  color: '#636',
});

let orangeSquare = new Zdog.Rect({
	addTo: illo,
	width: 80,  height: 80,
	translate: { z: -40 },
	stroke: 12,  color: '#E62',  fill: true,
});

</script>

Drag the illustration to view it from a different angle.

As usual, hit F12 or Ctrl-Shift-I to open the developer tools, and go to the Console tab.

Try changing the color or the stroke width of a shape: `purpleCircle.stroke = 30`

If you change the dimensions of a shape, you'll have to call e.g. `orangeSquare.updatePath()` to make your changes visible. If you set `width` and `height` on the circle (to make it an ellipse), you can `delete purpleCircle.width` and height to get back to using the `diameter`.

You could also try adding new shapes: see [the documentation](https://zzz.dog/shapes).

Remove or re-add an existing shape with `illo.removeChild(shape)` or `illo.addChild(shape)`.

The shapes were created with:

```javascript
let purpleCircle = new Zdog.Ellipse({
	addTo: illo,
	diameter: 80,
	translate: { z: 40 },
	stroke: 20,  color: '#636',
});

let orangeSquare = new Zdog.Rect({
	addTo: illo,
	width: 80,  height: 80,
	translate: { z: -40 },
	stroke: 12,  color: '#E62',  fill: true,
});
```
