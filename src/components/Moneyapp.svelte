<script>
  import Moneybox from './Moneybox.svelte';
  let type;
  let def_height = 300;
  let big_height = 1000;
  let bills_small = [{x1: 0, x2: 50, w:20},{x1: 100, x2: 150, w:20},{x1: 200, x2: 250, w:20},{x1: 300, x2: 350, w:20},{x1: 400, x2: 450, w:20},
  {x1: 500, x2: 550, w:20},{x1: 600, x2: 650, w:20},{x1: 700, x2: 750, w:20},{x1: 800, x2: 850, w:20},{x1: 900, x2: 950, w:20}];

  let bills_big = [{x1: 0, x2: 95, w:50},{x1: 100, x2: 195, w:50},{x1: 200, x2: 295, w:50},{x1: 300, x2: 395, w:50},{x1: 400, x2: 495, w:50},
  {x1: 500, x2: 595, w:50},{x1: 700, x2: 795, w:50},{x1: 600, x2: 695, w:50},{x1: 800, x2: 895, w:50},{x1: 900, x2: 995, w:50}];

  let def_rows = [0]
  let five_rows = [0,1,2,3,4,5];
  let header1 = 'This is $1000'
  let body1 = 'A decent amount of money'
  let billsv1 = '$100'

  let billsv2 = '$1,000'
  let header2 = 'This is $10000'
  let body2 = 'A lot of money!'

  let billsv3 = '$10,000'
  let header3 = 'This is $500,000'
  let body3 = 'A lot, but not even a milly!'
</script>

<main>
  <div class="greet">
    <h1>The scale of money</h1>
    <p>To help conceptualize how much X dollars is, the user will scroll down the page
      while Y dollar bills draw in section by section. </p>
    <p>
      X is an amount of money that can easily change the average person's life, especially if they are struggling.
    </p>
  </div>
  <div class="full-height">
    <Moneybox 
    bind:bills={bills_small}
    bind:headertext={header1}
    bind:bodytext={body1}
    bind:billsvalue={billsv1}
    bind:height={def_height}
    bind:rows={def_rows} />
  </div>
  <div class="full-height">
    <Moneybox
    bind:bills={bills_big}
    bind:headertext={header2}
    bind:bodytext={body2}
    bind:billsvalue={billsv2}
    bind:height={def_height}
    bind:rows={def_rows} />
  </div>
  <div class="full-height">
    <Moneybox
    bind:bills={bills_big}
    bind:headertext={header3}
    bind:bodytext={body3}
    bind:billsvalue={billsv3}
    bind:height={big_height}
    bind:rows={five_rows} />
  </div>
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  main {
    text-align: center;
    padding: 0 1em;
    margin: 0 auto;
  }

  h1 {
    margin-bottom: 0.5rem;
  }

  p {
    margin-top: 0;
  }

  .greet {
    height: calc(100vh - 16px);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .full-height {
    height: 80vh;
    display: flex;
    justify-content: center;
  }
</style>
