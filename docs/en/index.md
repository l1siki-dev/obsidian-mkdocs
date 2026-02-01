# My Project Documentation

Here is the architecture diagram:

<div 
  class="json-canvas-container" 
  data-src="canvas/demo.canvas" 
  style="width: 100%; height: 600px; border: 1px solid #ddd;">
</div>

<script type="module">
import CanvasViewer from "https://esm.sh/json-canvas-viewer@latest";

document.addEventListener("DOMContentLoaded", () => {
  const containers = document.querySelectorAll(".json-canvas-container");

  containers.forEach((container) => {
    // 1. Get the path to the .canvas file
    const canvasPath = container.getAttribute("data-src");
    if (!canvasPath) return;

    // 2. Ensure container has dimensions (critical!)
    // If not set in CSS, we force a default here to prevent collapse
    if (!container.style.height) {
      container.style.height = "600px";
    }
    if (!container.style.position) {
      container.style.position = "relative"; // Library needs this
    }

    try {
      // 3. Initialize the viewer
      // The library clears the container and sets up the stage
      const viewer = new CanvasViewer(container);

      // 4. Load the file by URL
      // This automatically handles the fetching and node parsing
      viewer.loadCanvas(canvasPath);

    } catch (err) {
      console.error("Canvas Viewer Error:", err);
      container.innerHTML = `<div style="padding:1rem; border:1px solid red; color:red;">
        <strong>Error loading canvas:</strong> ${err.message}
      </div>`;
    }
  });
});
</script>
