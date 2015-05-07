# Scamper
Even points along a cubic Bezier curve


### Usage

```js
var isDrawing = false;
var scamper = new Scamper({step: 10, sample: 2});

scamper.setHandlePointFunction(function(pt) {
	var d = document.createElement("div");
	d.innerHTML = 's';
	d.setAttribute('style', 'position: absolute; top: ' + pt.y + 'px; left: ' + pt.x + 'px;');
	document.body.appendChild(d);
});

window.onmousedown = function(e) {
	isDrawing = true;
	scamper.newStroke();
	scamper.addPoint(
	  e.clientX,
	  e.clientY,
	  0
	);
}
window.onmousemove = function(e) {
	if (!isDrawing) return;
	scamper.addPoint(
	  e.clientX,
	  e.clientY,
	  0
	);
}
window.onmouseup = function(e) {
	isDrawing = false;
	scamper.addPoint(
	  e.clientX,
	  e.clientY,
	  0
	);
}
```
