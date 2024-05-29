<script>
  import { onMount } from "svelte";

  let canvas;
  let ctx;

  onMount(() => {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
    ctx = canvas.getContext("2d");

    function random(min, max) {
      return Math.random() * (max - min) + min;
    }

    function drawLightningSegment(x, y, xEnd, yEnd, branchWidth, alpha) {
      ctx.strokeStyle = `rgba(255, 255, 255, ${alpha})`;
      ctx.lineWidth = branchWidth;
      ctx.beginPath();
      ctx.moveTo(x, y);
      ctx.lineTo(xEnd, yEnd);
      ctx.stroke();
    }

    function drawLightning(x, y, xEnd, yEnd, branchWidth) {
      let segments = 20;
      let lightningPath = [];
      let curX = x;
      let curY = y;
      lightningPath.push({ x: curX, y: curY });

      for (let i = 0; i < segments; i++) {
        curX += (xEnd - x) / segments + random(-20, 20);
        curY += (yEnd - y) / segments + random(-20, 20);
        lightningPath.push({ x: curX, y: curY });
      }

      lightningPath.push({ x: xEnd, y: yEnd });

      let i = 0;
      let alpha = 1;
      function animateLightning() {
        if (i < lightningPath.length - 1) {
          drawLightningSegment(
            lightningPath[i].x,
            lightningPath[i].y,
            lightningPath[i + 1].x,
            lightningPath[i + 1].y,
            branchWidth,
            alpha
          );
          i++;
          requestAnimationFrame(animateLightning);
        } else {
          fadeLightning(lightningPath, branchWidth, alpha);
        }
      }

      function fadeLightning(path, branchWidth, alpha) {
        if (alpha > 0) {
          ctx.clearRect(0, 0, canvas.width, canvas.height); // Clear the previous frame
          alpha -= 0.02; // Adjust fade speed here
          for (let j = 0; j < path.length - 1; j++) {
            drawLightningSegment(
              path[j].x,
              path[j].y,
              path[j + 1].x,
              path[j + 1].y,
              branchWidth,
              alpha
            );
          }
          requestAnimationFrame(() => fadeLightning(path, branchWidth, alpha));
        }
      }

      animateLightning();
    }

    function createFlash() {
      ctx.globalCompositeOperation = "lighter";
      let xStart = random(0, canvas.width);
      let yStart = 0;
      let xEnd = random(0, canvas.width);
      let yEnd = canvas.height;
      drawLightning(xStart, yStart, xEnd, yEnd, 2);
      drawLightning(
        random(0, canvas.width),
        0,
        random(0, canvas.width),
        canvas.height,
        1
      );
    }

    function startLightning() {
      createFlash();
      setTimeout(startLightning, random(1500, 3000)); // More frequent lightning
    }

    startLightning();
  });
</script>

<canvas
  bind:this={canvas}
  style="position: fixed; top: 0; left: 0; z-index: 100;"
></canvas>

<style>
  canvas {
    width: 100%;
    height: 100%;
  }
</style>
