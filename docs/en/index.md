# My Project Documentation

Here is the architecture diagram:

<div 
  class="json-canvas-container" 
  data-src="canvas/demo.canvas" 
  style="width: 100%; height: 600px; border: 1px solid #ddd;">
</div>

<script type="module">
import { CanvasViewer } from "https://esm.sh/json-canvas-viewer@latest";

// Wrapper to run logic
const initCanvases = () => {
  const containers = document.querySelectorAll(".json-canvas-container");
  containers.forEach((container) => {
    if (container.getAttribute("data-loaded")) return; // Prevent double-load
    
    const canvasPath = container.getAttribute("data-src");
    if (!canvasPath) return;

    // Set dimensions if missing
    if (!container.style.height) container.style.height = "600px";
    
    try {
      const viewer = new CanvasViewer(container);
      viewer.loadCanvas(canvasPath);
      container.setAttribute("data-loaded", "true"); // Mark as processed
    } catch (err) {
      console.error(err);
    }
  });
};

// Hook for standard load
document.addEventListener("DOMContentLoaded", initCanvases);

// Hook for MkDocs Material Instant Loading (if used)
if (window.document$) {
  window.document$.subscribe(() => {
    initCanvases();
  });
}
</script>
