<script lang="ts">
    import { fade } from 'svelte/transition';
    import { fly, draw } from "svelte/transition";
    import { cubicOut, cubicInOut } from "svelte/easing";
    import { inview } from 'svelte-inview';
    import { onMount } from 'svelte';

    export let bills;
    export let billsvalue;
    export let headertext;
    export let bodytext;
    export let height;
    export let rows;
    export let speed;
    let index = 10;
    let isInView;

  </script>
  
  <div
    class="wrapper"
    use:inview={{ unobserveOnEnter: false, rootMargin: '-20%' }}
    on:change={({ detail }) => {
      isInView = detail.inView;
    }}
  >
    {#if isInView}
      <div in:fade out:fade class="box">
        <h3>{headertext}</h3>
        <svg width = 1000 height = {height/2}>
          {#each rows as row}
            {#each bills as bill}
              <line
              x1 = {bill.x1}
              x2 = {bill.x2}
              y1 = {row*(bill.x2-bill.x1)/1.5 + 50}
              y2 = {row*(bill.x2-bill.x1)/1.5 + 50}
              stroke-width = {bill.w}
              stroke = '#85bb65'
              transition:draw|global={{ delay: (bill.x1*1.1 + row*1000)/speed, duration: 500, easing: cubicInOut }}
              />
              <text
              font-size = {bill.w*0.4 + 3}
              x = {(bill.x1+bill.x2)/2}
              y={row*(bill.x2-bill.x1)/1.5 + 50 + 5}
              text-anchor = 'middle'
              in:fade|global={{ delay: (bill.x1 + row*1000 + 500)/speed, duration:500}}
              >
              {billsvalue}
              </text>
            {/each}
          {/each}

        </svg>
        
        <p>
          {bodytext}
        </p>
      </div>
    {/if}
  </div>
  
  <style>
    .wrapper {
      margin-top: 30px;
    }
  
    .box {
      width: 1000px;
      border: 3px solid rgba(121, 109, 194, 0.55);
      padding: 25px;
      border-radius: 10px;
      background-color: rgba(138, 128, 209, 0.185);
    }
  </style>
  