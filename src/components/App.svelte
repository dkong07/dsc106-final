<script>
  // Write your JS here, or import other files
  import * as d3 from 'd3';
  import { onMount } from 'svelte';

  //This is Jill's large people visualization
  import LargePeople from './LargePeople.svelte';

  let large_people_data = [];

  onMount(async () => {
    large_people_data = await d3.csv('large_people_2.csv', d3.autoType);

  });
  
  import SmallNums from './SmallNums(working).svelte'
  import Moneyapp from './Moneyapp.svelte';
</script>

<main>
  <h1>Visualizing Numbers</h1>

  <p>
    The interesting phenomenon our group wants to focus on is how humans struggle to understand the scale of numbers, both large and small.
    <br>
    How much is 1000, or one million, a billion, or more? How small is e-4? or e-10?
    <br>
    Our group aims to visually illustrate how much humans underestimate these scales, and how difficult they can be to interpret without a visual guide. 
  </p>

  <!-- <h2>Visualizing large numbers of people</h2> -->
  {#if large_people_data.length === 0}
    <p>Loading...</p>
  {:else}
    <LargePeople {large_people_data} />
  {/if}
  
  <p>
    Ever wondered how small molecules really are? Water moluecules are about 0.27 nanometers across, but what does that really mean?
    <br>
    The width of the brown box below represents the width of an average human hair. Along the hair, water molecules are lined up side by side.
    <br>
    Cant see them? Try zooming in
  </p>

  <div id='small nums'>
    <SmallNums/> 
  </div>


  <div id='money'>
    <Moneyapp/>
  </div>
</main>

<style>
  /* .main{
    background-color: blanchedalmond;
  } */
</style>
