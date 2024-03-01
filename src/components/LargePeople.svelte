<script>
export let large_people_data;

import { onMount } from 'svelte';
import * as d3 from 'd3';

const width = 1500;
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

let spacingwidth = 50
let spacingwidth_1 = 40
let spacingheight  = 20

let page_on = 1;

function handleClick_in() {
    if (page_on == 1){
        alert("Can't zoom in from one person!!");
    }
    else{
        document.getElementById('Row' + page_on).style.display = 'none';
        // Move to the next group
        page_on -= 1;
        
        
        // Show the next group
        document.getElementById('Row' + page_on).style.display = 'block';
    }
  }

function handleClick_out() {
    if (page_on == 5){
        alert("This is all we have! Can you think of how population in SD can scale up?");
    }
    else{
        document.getElementById('Row' + page_on).style.display = 'none';
        // Move to the next group
        page_on += 1;
        
        
        // Show the next group
        document.getElementById('Row' + page_on).style.display = 'block';
    }
  }

function createButton_in() {
    d3.select('.zoom_in') // Select the container element
      .append('button') // Append a button element
      .text('Scope in') // Set the text content of the button
      .on('click', handleClick_in); // Add a click event listener
  }

function createButton_out() {
    d3.select('.zoom_out') // Select the container element
      .append('button') // Append a button element
      .text('Scope out') // Set the text content of the button
      .on('click', handleClick_out); // Add a click event listener
  }

onMount(() => {
    createButton_in();
    createButton_out();
  });

</script>

<div class = 'buttons'>
    <div class="zoom_in"></div> 
    <div class="zoom_out"></div>
</div>

<svg {width} {height} viewBox="0 0 {width} {height}" >
    <g stroke="black" stroke-width="0.5" transform="translate(0, 20)" class = "layer" id = 'Row1'>
        <text transform="translate(100, 50)" font-size="75">{firstRow['Stat']}</text>
        <text font-size="25" transform="translate(0, 80)"> Description: {firstRow['Data_descipt']}</text>
    </g>
    <g stroke="black" stroke-width="0.5" transform="translate(0,20)" class = "layer" id = 'Row2'>
        <g>
            {#each iterations10 as i, indexh}
                {#each iterations10 as j, index}
                    <text x={index * spacingwidth_1} y={indexh * spacingheight}>{firstRow['Stat']}</text>
                {/each}
            {/each}
        </g>
        <g>
            <text font-size="50" transform="translate(450, 100)"> = 100 people</text>
        </g>
        <text font-size="25" transform="translate(0, 220)"> Description: {secondRow['Data_descipt']}</text>
    </g>
    <g stroke="black" stroke-width="0.5" transform="translate(0, 20)" class = "layer" id = 'Row3'>
        <g>
            {#each iterations5 as i, indexh}
                {#each iterations6 as j, index}
                    <text x={index * spacingwidth} y={indexh * spacingheight}>{secondRow['Stat']}</text>
                {/each}
            {/each}
        </g>
        <g>
            <text font-size="50" transform="translate(400, 50)"> = </text>
            <text font-size="40" transform="translate(450, 20)"> 30 rooms of DSC 106 student watching demo</text>
            <text font-size="40" transform="translate(450, 80)"> 3K people</text>
        </g>
        <text font-size="25" transform="translate(0, 120)"> Description: {thirdRow['Data_descipt']}</text>
    </g>
    <g stroke="black" stroke-width="0.5" transform="translate(0, 20)" class = "layer" id = 'Row4'>
        <g>
            {#each iterations4 as i, indexh}
                {#each iterations6 as j, index}
                    <text x={index * spacingwidth} y={indexh * spacingheight}>{thirdRow['Stat']}</text>
                {/each}
            {/each}
        </g>
        <g>
            <text font-size="50" transform="translate(400, 50)"> = </text>
            <text font-size="40" transform="translate(450, 20)"> 24 twitch streamer with 3000 daily views</text>
            <text font-size="40" transform="translate(450, 80)"> 70K people</text>
        </g>
        <text font-size="25" transform="translate(0, 100)"> Description: {forthRow['Data_descipt']}</text>
    </g>
    <g stroke="black" stroke-width="0.5" transform="translate(0, 20)" class = "layer" id = 'Row5'>
        <g>
            {#each iterations4 as i, indexh}
                {#each iterations5 as j, index}
                    <text x={index * spacingwidth} y={indexh * spacingheight}>{forthRow['Stat']}</text>
                {/each}
            {/each}
        </g>
        <g>
            <text font-size="50" transform="translate(400, 50)"> = </text>
            <text font-size="40" transform="translate(450, 20)"> 15 Sofi Stadium</text>
            <text font-size="40" transform="translate(450, 80)"> 1.3M  people</text>
        </g>
        <text font-size="25" transform="translate(0, 90)"> Description: {fifthRow['Data_descipt']}</text>
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
    margin-right: 10px; /* Add some margin between buttons */
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

</style>