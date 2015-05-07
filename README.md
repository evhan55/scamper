# Scamper

Scamper takes raw input points and maps them to evenly spaced points along a cubic Bezier curve.

### API

<table>
<tr>
  <td width="30%"><code>Scamper(opts)</code></td>
  <td width="70%">Creates a new Scamper instance.  Optional parameters: <br> <b>sample</b>: point subsampling rate <br> <b>step</b>: desired distance between points</td>
</tr>
</table>

<table>
<tr>
  <td width="30%"><code>newStroke()</code></td>
  <td width="70%">Begins a new stroke.</td>
</tr>
<tr>
  <td><code>addPoint(x, y, p)</code></td>
  <td>Adds raw input point to current stroke.</td>
</tr>
<tr>
  <td><code>setPointHandler(function)</code></td>
  <td>Function to be run on new even step points.</td>
</tr>
</table>

### Usage

```js
var isDrawing = false;
var scamper = new Scamper({step: 10, sample: 2});

scamper.setPointHandler(function(pt) {
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
