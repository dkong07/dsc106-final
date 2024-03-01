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
    ctx.strokeStyle = '#8B4513'; 
    ctx.stroke();

    const numberOfMolecules = (hairWidthNm/waterMoleculeLengthNm)/zoom
    const step = 1200/numberOfMolecules
    
    for (let i = 0; i < numberOfMolecules; i++) {
      ctx.beginPath();
      const xPosition = i * step;
      ctx.arc(xPosition, 100, 0.002 * zoom, 0, 2 * Math.PI);
      ctx.fillStyle = 'blue';
      ctx.fill();
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
    <label for="zoom">Zoom:</label>
    <input type="range" id="zoom" min="1" max="10000" value={zoom} on:input="{e => zoom = +e.target.value}" />
    <span>{"Multiplier: "}{zoom}</span>
</div>
<canvas id="visualizationCanvas" width="1200" height="200" style="border: 1px solid black;"></canvas>
