<script>
  // Write your JS here, or import other files
  import * as d3 from 'd3';
  import LargePeople from './LargePeople.svelte';
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
  
  <p>
    Ever wondered how small molecules really are? Water moluecules are about 0.27 nanometers across, but what does that really mean?
    <br>
    The width of the brown box below represents the width of an average human hair. Along the hair, water molecules are lined up side by side.
    <br>
    Cant see them? Try zooming in
  </p>
  <div id='small nums'>
    <SmallNums /> 
  </div>


  <div id='money'>
    <Moneyapp/>
  </div>
</main>

<style>
  .main{
    background-color: blanchedalmond;
  }
</style>
