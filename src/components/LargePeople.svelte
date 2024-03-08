<script>
export let large_people_data;

import { onMount } from 'svelte';
import * as d3 from 'd3';

const width = 1300;
const height = 300;

export const firstRow = large_people_data[0]
export const secondRow = large_people_data[1]
export const thirdRow = large_people_data[2]
export const forthRow = large_people_data[3]
export const fifthRow = large_people_data[4]

const iterations4 = Array.from({ length: 4 }, (_, index) => index + 1);
const iterations5 = Array.from({ length: 5 }, (_, index) => index + 1);
const iterations6 = Array.from({ length: 6 }, (_, index) => index + 1);
const iterations10 = Array.from({ length: 10 }, (_, index) => index + 1);

let spacingwidth = 60
let spacingheight  = 50
let spacingwidth_1 = 40
let spacingheight_1  = 20


let page_on = 1;

function handleClick_in() {
    if (page_on == 1){
        alert("Can't zoom in from one person!!");
    }
    else{
        // document.getElementById('Row' + page_on).style.display = 'none';
        var currentPage = document.getElementById('Row' + page_on);
        currentPage.style.transition = 'opacity 1s ease';
        currentPage.style.opacity = '0';
        currentPage.style.display = 'none';


        // Move to the next group
        page_on -= 1;
        
        
        // Show the next group
        // document.getElementById('Row' + page_on).style.display = 'block';
        setTimeout(function() {
            var prevPage = document.getElementById('Row' + page_on);
            prevPage.style.transition = 'opacity 1s ease';
            prevPage.style.opacity = '1';
            prevPage.style.display = 'block';

        }, 500); // Wait for the transition duration
    }
  }

function handleClick_out() {
    if (page_on == 5){
        alert("This is all we have! Can you think of how population in SD can scale up?");
    }
    else{
        // document.getElementById('Row' + page_on).style.display = 'none';
        var currentPage = document.getElementById('Row' + page_on);
        currentPage.style.transition = 'opacity 1s ease';
        currentPage.style.opacity = '0';
        currentPage.style.display = 'none';

        // Move to the next group
        page_on += 1;
        
        
        // Show the next group
        // document.getElementById('Row' + page_on).style.display = 'block';
        setTimeout(function() {
            var nextPage = document.getElementById('Row' + page_on);
            nextPage.style.transition = 'opacity 1s ease';
            nextPage.style.opacity = '1';
            nextPage.style.display = 'block';

        }, 500); // Wait for the transition duration
    }
  }

function createButton_in() {
    d3.select('.zoom_in') // Select the container element
      .append('button') // Append a button element
      .text('Scope in') // Set the text content of the button
      .on('click', handleClick_in) // Add a click event listener
      .style('font-size', '18px') // Set the font size
      .style('font-family', 'Arial, sans-serif'); // Set the font family
  }

function createButton_out() {
    d3.select('.zoom_out') // Select the container element
      .append('button') // Append a button element
      .text('Scope out') // Set the text content of the button
      .on('click', handleClick_out) // Add a click event listener
      .style('font-size', '18px') // Set the font size
      .style('font-family', 'Arial, sans-serif'); // Set the font family
  }

onMount(() => {
    createButton_in();
    createButton_out();
  });

</script>
<div class = 'everything'>
<br>
<h2>Visualizing large numbers of peoples</h2>

<p>
    The rise to the internet has allowed people to make connections around the world and this has lead to a popularity in multiple social media platform such as Instagram, Tiktok, Twitch, etc
    <br>
    These platform oftem has their own ways of quantifying popularity of those users through likes and views. 
    <br><br>
    Us group first wants to get your attention of do you really understand what these numbers look like? 
    <br>
    For example, when you see 500K views on TikTok, we all agree that it is a large number, but have you ever imagined how much 500K of people look like? It doesn't even fit a largest stadium in the world!
    <br>
    These numbers can scale up really quickly, but when you put into perspective that each 1s that make up these huge numbers are actual human, we have difficulties understanding them. 
    <br>
    This visualization below is intended to show you how much these numbers of people can scale up to give you a better understanding of how large population can look like. 
</p>

<div class = 'buttons'>
    <div class="zoom_in"></div> 
    <div class="zoom_out"></div>
</div>
</div>

<svg {width} {height} viewBox="0 0 {width} {height}">
    <g stroke="black" stroke-width="0.5" transform="translate(120, 80)" class = "layer" id = 'Row1'>
        <text transform="translate(100, 50)" font-size="75">{firstRow['Stat']}</text>
        <text font-size="25" transform="translate(0, 80)"> Description: {firstRow['Data_descipt']}</text>
    </g>
    <g stroke="black" stroke-width="0.5" transform="translate(0,40)" class = "layer" id = 'Row2'>
        <g transform="translate(30, 0)">
            {#each iterations10 as i, indexh}
                {#each iterations10 as j, index}
                    <text x={index * spacingwidth_1} y={indexh * spacingheight_1}>{firstRow['Stat']}</text>
                {/each}
            {/each}
        </g>
        <g>
            <text font-size="50" transform="translate(450, 100)" fill="blue"> = 100 people</text>
        </g>
        <text font-size="25" transform="translate(0, 220)"> Description: {secondRow['Data_descipt']}</text>
    </g>
    <g stroke="black" stroke-width="0.5" class = "layer" id = 'Row3'>
        <g transform="translate(30, 60)" font-size="20">
            {#each iterations5 as i, indexh}
                {#each iterations6 as j, index}
                    <text fill="blue" x={index * spacingwidth} y={indexh * spacingheight}>{secondRow['Stat']}</text>
                {/each}
            {/each}
        </g>
        <g>
            <text font-size="50" transform="translate(400, 160)"> = </text>
            <text font-size="40" transform="translate(450, 130)" fill="brown"> 30 rooms of DSC 106 student watching demo</text>
            <text font-size="40" transform="translate(450, 190)" fill="brown"> 3K people</text>
        </g>
        <text font-size="25" transform="translate(0, 295)"> Description: {thirdRow['Data_descipt']}</text>
    </g>
    <g stroke="black" stroke-width="0.5" class = "layer" id = 'Row4'>
        <g transform="translate(10, 80)" font-size="25">
            {#each iterations4 as i, indexh}
                {#each iterations6 as j, index}
                    <text fill="brown" x={index * 65} y={indexh * spacingheight}>{thirdRow['Stat']}</text>
                {/each}
            {/each}
        </g>
        <g>
            <text font-size="50" transform="translate(400, 160)"> = </text>
            <text font-size="40" transform="translate(450, 130)" fill="green"> 24 twitch streamer with 3000 views</text>
            <text font-size="40" transform="translate(450, 190)" fill="green"> 70K people</text>
        </g>
        <text font-size="25" transform="translate(0, 280)"> Description: {forthRow['Data_descipt']}</text>
    </g>
    <g stroke="black" stroke-width="0.5" class = "layer" id = 'Row5'>
        <g transform="translate(0, 80)" font-size="25">
            {#each iterations4 as i, indexh}
                {#each iterations5 as j, index}
                    <text fill="green" x={index * 80} y={indexh * spacingheight}>{forthRow['Stat']}</text>
                {/each}
            {/each}
        </g>
        <g>
            <text font-size="50" transform="translate(400, 160)"> = </text>
            <text font-size="40" transform="translate(450, 130)" fill="red"> 15 Sofi Stadium</text>
            <text font-size="40" transform="translate(450, 190)" fill="red"> 1.3M  people</text>
        </g>
        <text font-size="25" transform="translate(0, 280)"> Description: {fifthRow['Data_descipt']}</text>
    </g>
</svg>


<style>
.buttons {
  display: flex; /* Use flexbox layout */
}

.zoom_in{
    width: 100px; /* Set width of each button */
    height: 40px; /* Set height of each button */
    margin-right: 10px; /* Add some margin between buttons */
    justify-content: center; /* Center content horizontally */
    align-items: center; /* Center content vertically */
    display: flex; /* Use flexbox layout for buttons */

    
}
.zoom_out {
    width: 100px; /* Set width of each button */
    height: 40px; /* Set height of each button */
    margin-right: 14px; /* Add some margin between buttons */
    display: flex; /* Use flexbox layout for buttons */
    justify-content: center; /* Center content horizontally */
    align-items: center; /* Center content vertically */
}

#Row2,
#Row3,
#Row4,
#Row5{
    display: none;
}

/* .everything { */
    /* display: flex; */
    /* text-align: center;
    justify-content: center;
    align-items: center;

    display: flex;
    flex-direction: column; */
    /* align-items: center; */
    /* justify-content: center; */
/* } */


</style>