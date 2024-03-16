<script>
  import Moneybox from './Moneybox.svelte';
  let type;
  let def_height = 300;
  let sm_height = 600;
  let mid_height = 800;
  let big_height = 1000;
  let massive = 10000;
  let bills_small = [{x1: 0, x2: 50, w:20},{x1: 100, x2: 150, w:20},{x1: 200, x2: 250, w:20},{x1: 300, x2: 350, w:20},{x1: 400, x2: 450, w:20},
  {x1: 500, x2: 550, w:20},{x1: 600, x2: 650, w:20},{x1: 700, x2: 750, w:20},{x1: 800, x2: 850, w:20},{x1: 900, x2: 950, w:20}];

  let bills_big = [{x1: 0, x2: 95, w:50},{x1: 100, x2: 195, w:50},{x1: 200, x2: 295, w:50},{x1: 300, x2: 395, w:50},{x1: 400, x2: 495, w:50},
  {x1: 500, x2: 595, w:50},{x1: 700, x2: 795, w:50},{x1: 600, x2: 695, w:50},{x1: 800, x2: 895, w:50},{x1: 900, x2: 995, w:50}];

  var b = Array.from(Array(20).keys()).map(function(x) { return x * 50; });
  let twentybills = b.map(val => ({ x1: val, x2: val+45, w:25 }))

  var a = Array.from(Array(100).keys()).map(function(x) { return x * 10; });
  let tinybills = a.map(val => ({ x1: val, x2: val+8, w:3 }))
  
  console.log(tinybills)
  
  let speedmax = 100;
  let speedfast=5;
  let speedmod=2.5;
  let normspeed=1;

  let def_rows = [0]
  let two_rows =[0,1]
  let ten_rows = [0,1,2,3,4,5,6,7,8,9]
  let five_rows = [0,1,2,3,4];
  let fifty = Array.from(Array(50).keys())
  let header1 = '$1000'
  let body1 = 'A good amount of money that no one would complain about, but fairly common.'
  let billsv1 = '$100'
  let billsv0 = ''
  let billsv2 = '$1,000'
  let header2 = '$10000'
  let body2 = 'A lot more money now. This could buy someone a car, prevent homelessness, or if lost, ruin someones life. But still, not even close to the top.'

  let billsv3 = '$10,000'
  let header3 = 'This is $500,000'
  let body3 = 'A lifechanging amount of money. Most people will never see this amount of money from the day they are born to the day they die in a single instance. '
  
  let headerv4 ='Lets see what that 500,000 looks like in 100 dollar bills.'
  let body4 = 'If these bills were worth 10,000 instead of 100 each, we would have about the value of ONE of Taylor Swifts private jets, or 50 million dollars. A single row of bills would be worth a million dollars.' 
</script>

<main>
  <div class="greet">
    <h1>The scale of money</h1>
    <p>To help conceptualize how much a certain amount of dollars is, the user will scroll down the page
      while representative dollar bills draw in section by section. </p>
    <p>
      Any amount of money could change someone's life and be meaningless to another. Let's scale these values so that they're easier to understand.
    </p>
  </div>
  <!--1000 bucks-->
  <div class="full-height">
    <Moneybox 
    bind:bills={bills_big}
    bind:headertext={header1}
    bind:bodytext={body1}
    bind:billsvalue={billsv1}
    bind:height={def_height}
    bind:rows={def_rows}
    bind:speed={normspeed} />
  </div>
 <!--10000 bucks-->
  <div class="full-height">
    <Moneybox
    bind:bills={bills_big}
    bind:headertext={header2}
    bind:bodytext={body2}
    bind:billsvalue={billsv1}
    bind:height={mid_height}
    bind:rows={ten_rows}
    bind:speed={speedfast} />
  </div>
 <!--50000 bucks-->
  <div class="full-height">
    <Moneybox
    bind:bills={bills_big}
    bind:headertext={header3}
    bind:bodytext={body3}
    bind:billsvalue={billsv3}
    bind:height={mid_height}
    bind:rows={five_rows}
    bind:speed={speedmod} />
  </div>
 <!--v2 50,000 bucks-->
  <div class="full-height">
    <Moneybox
    bind:bills={tinybills}
    bind:headertext={headerv4}
    bind:bodytext={body4}
    bind:billsvalue={billsv0}
    bind:height={sm_height}
    bind:rows={fifty}
    bind:speed={speedmod} />
  </div>
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  main {
    text-align: center;
    padding: 0 0.1em;
    margin: 0 auto;
  }

  h1 {
    margin-bottom: 0.3rem;
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
