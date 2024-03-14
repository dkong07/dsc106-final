<script>
  import { onMount } from 'svelte';

  let zoom = 1; //initialize zoom

  const hairWidthNm = 80000;
  const waterMoleculeLengthNm = 0.27;

  function draw() {
    const canvas = document.getElementById('visualizationCanvas');
    if (!canvas) return;
    const ctx = canvas.getContext('2d');
    canvas.width = canvas.width; //clear the canvas

    ctx.beginPath();
    ctx.moveTo(0, 100);
    ctx.lineTo(1200, 100);
    ctx.lineWidth = 200;
    ctx.strokeStyle = '#B8833F'; 
    ctx.stroke();

    ctx.font = '20px Arial';
    ctx.fillStyle = 'black';
    ctx.fillText(`Width of human hair ➗ ${zoom}`, 500, 160);

    const numberOfMolecules = (hairWidthNm/waterMoleculeLengthNm)/zoom
    const step = 1200/numberOfMolecules
    
    for (let i = 0; i < numberOfMolecules; i++) {
      ctx.beginPath();
      const xPosition = i * step;
      ctx.arc(xPosition, 100, 0.002 * zoom, 0, 2 * Math.PI);
      ctx.fillStyle = 'blue';
      ctx.fill();
    }

    ctx.beginPath();
    ctx.moveTo(0, 180); 
    ctx.lineTo(1200, 180);
    ctx.lineWidth = 5;
    ctx.strokeStyle = 'black'; 
    ctx.stroke();

    ctx.beginPath();
    ctx.moveTo(2, 160); 
    ctx.lineTo(2, 200); 
    ctx.lineWidth = 5;
    ctx.stroke();

    ctx.beginPath();
    ctx.moveTo(1198, 160); 
    ctx.lineTo(1198, 200);
    ctx.lineWidth = 5;
    ctx.stroke();  
  }
  function setZoom(level) {
    zoom = level;
  }

  onMount(() => {
    draw();
  });

  $: if (typeof window !== 'undefined') {
    console.log(zoom); 
    draw();
}
</script>

<div>
  <button on:click="{() => setZoom(100)}">Zoom 100x</button>
  <button on:click="{() => setZoom(5000)}">Zoom 5,000x</button>
  <button on:click="{() => setZoom(10000)}">Zoom 10,000x</button>
  <label for="zoom">Zoom:</label>
  <input type="range" id="zoom" min="1" max="10000" value={zoom} on:input="{e => zoom = +e.target.value}" />
</div>
<canvas id="visualizationCanvas" width="1200" height="200" style="border: 1px solid black;"></canvas>
