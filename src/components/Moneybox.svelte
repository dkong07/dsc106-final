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
        <svg width = 1000 height = {height/2}>
          {#each rows as row}
            {#each bills as bill}
              <line
              x1 = {bill.x1}
              x2 = {bill.x2}
              y1 = {row*100 + 50}
              y2 = {row*100 + 50}
              stroke-width = {bill.w}
              stroke = '#85bb65'
              transition:draw|global={{ delay: 100, duration: 1000, easing: cubicInOut }}
              />
              <text
              font-size = {bill.w*0.4 + 3}
              x = {(bill.x1+bill.x2)/2}
              y={row*100 + 55}
              text-anchor = 'middle'
              in:fade|global={{ delay: 1200, duration:500}}
              >
              {billsvalue}
              </text>
            {/each}
          {/each}

        </svg>
        <h3>{headertext}</h3>
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
      border: 1px solid rgb(221, 221, 221);
      padding: 25px;
      border-radius: 10px;
    }
  </style>
  