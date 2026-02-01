# My Project Documentation

Here is the architecture diagram:

<div 
  class="json-canvas-container" 
  data-src="canvas/index.canvas" 
  style="width: 100%; height: 600px; border: 1px solid #ddd;">
</div>

<script type="module">
  import { JSONCanvasViewer } from "https://esm.sh/json-canvas-viewer@latest";
  document.addEventListener("DOMContentLoaded", () => {
    // Find all containers we want to turn into canvases
    const containers = document.querySelectorAll(".json-canvas-container");

    containers.forEach(async (container) => {
      const canvasPath = container.getAttribute("data-src");
      
      if (!canvasPath) return;

      // 1. Fetch the .canvas file content
      try {
        const response = await fetch(canvasPath);
        if (!response.ok) throw new Error(`Failed to load ${canvasPath}`);
        const canvasData = await response.json();

        // 2. Initialize the viewer
        // Clean the container first just in case
        container.innerHTML = "";
        
        const viewer = new JSONCanvasViewer(container);
        
        // 3. Load the data into the viewer
        // The library API might vary slightly by version, but typically:
        viewer.loadData(canvasData);

      } catch (err) {
        console.error(err);
        container.innerHTML = `<p style="color:red">Error loading canvas: ${err.message}</p>`;
      }
    });
  });
</script>
