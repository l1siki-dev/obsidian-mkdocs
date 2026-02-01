<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8" />
	<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
	<title>🐒 Canvas Viewer</title>
	<style>
		body, html {
			margin: 0;
			padding: 0;
			width: 100%;
			height: 100%;
		}
	</style>
</head>
<body></body>
<script type="module">
import { JSONCanvasViewer, parser, loadCanvas } from 'https://unpkg.com/json-canvas-viewer/dist/chimp.js';
new JSONCanvasViewer({
    container: document.body, // The element to attach the viewer to
    canvas: loadCanvas('\en\index.canvas'),  // remember to prepare your canvas
    markdownParser: parser,
});
</script>
</html>