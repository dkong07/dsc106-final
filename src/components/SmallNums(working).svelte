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
    ctx.fillText(`Width of human hair ➗ ${zoom}`, 500, 250);

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
    ctx.moveTo(0, 220); 
    ctx.lineTo(1200, 220);
    ctx.lineWidth = 5;
    ctx.strokeStyle = 'black'; 
    ctx.stroke();

    ctx.beginPath();
    ctx.moveTo(2, 200); 
    ctx.lineTo(2, 240); 
    ctx.lineWidth = 5;
    ctx.stroke();

    ctx.beginPath();
    ctx.moveTo(1198, 200); 
    ctx.lineTo(1198, 240);
    ctx.lineWidth = 5;
    ctx.stroke();  

    if (zoom === 10000) {
    ctx.font = '20px Arial';
    ctx.fillStyle = 'black';
    ctx.fillText(`(MAX ZOOM)`, 570, 170);
    }
  }
  function resetZoom(input){
    zoom = input
  }
  function setZoom(level) {
    if ((zoom*level) <= 10000){
      zoom = zoom*level
    } else {
      zoom = 10000
    }  
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
  <button on:click="{() => resetZoom(1)}">Reset Zoom</button>
  <button on:click="{() => setZoom(2)}">Zoom 2x</button>
  <button on:click="{() => setZoom(100)}">Zoom 100x</button>
  <button on:click="{() => setZoom(10000)}">Max Zoom</button>
  <label for="zoom">Zoom:</label>
  <input type="range" id="zoom" min="1" max="10000" value={zoom} on:input="{e => zoom = +e.target.value}" />
</div>
<canvas id="visualizationCanvas" width="1200" height="260" style="border: 1px solid black;"></canvas>
