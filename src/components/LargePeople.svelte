<script>
export let large_people_data;

import { onMount } from 'svelte';
import * as d3 from 'd3';

const width = 800;
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
let mouseX = 0;
let mouseY = 0;
let tooltipOffsetX = 10; 
let tooltipOffsetY = -20;

let isHovered = false;

  function handleMouseOver() {
    isHovered = true; 
    updateTooltipPosition(event);

  }

  function handleMouseOut() {
    isHovered = false; 
  }
  
  function updateTooltipPosition(event) {
    const svgRect = event.target.getBoundingClientRect();

    mouseX = event.clientX + tooltipOffsetX;
    mouseY = event.clientY + tooltipOffsetY;

  }

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

        }, 500);
        console.log(page_on)
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

        }, 500); 
        console.log(page_on)
    }
  }

function createButton_in() {
    d3.select('.zoom_in') 
      .append('button') 
      .text('Scope in') 
      .on('click', handleClick_in) 
      .style('font-size', '28px') 
      .style('font-family', 'VT323, monospace') 
      .style('width', '130px') 
      .style('height', '45px') 
      .style('background-color', 'lavender'); 

  }

function createButton_out() {
    d3.select('.zoom_out') 
      .append('button') 
      .text('Scope out') 
      .on('click', handleClick_out) 
      .style('font-size', '28px') 
      .style('font-family', 'VT323, monospace') 
      .style('width', '130px') 
      .style('height', '45px') 
      .style('background-color', 'lavender'); 
  }

onMount(() => {
    createButton_in();
    createButton_out();
  });

</script>
<br>
<h2>Part 1: Visualizing large numbers of peoples</h2>

<p>
    The rise of the internet has allowed people to make connections around the world and this has led to popularity in multiple social media platforms such as Instagram, TikTok, Twitch, etc    <br>
    These platforms often have their ways of quantifying the popularity of those users through likes and views.
    <br><br>
    Our group first wants to get your attention to ask if you understand what these numbers look like.
    <br>
    For example, when you see 500K views on TikTok, we all agree that it is a large number, but have you ever imagined how much 500K people look like? It doesn't even fit the largest stadium in the world!
    <br>
    These numbers can scale up quickly, but when you put into perspective that each 1s that make up these huge numbers is human, we have difficulties understanding them.
    <br><br>
    This visualization below is intended to show you how much these numbers of people can scale up to give you a better understanding of what a large population can look like.
    <br>
    Click on the "Scope in" and "Scope out" buttons to toggle through the scale!
</p>

<div class = 'buttons'>
    <div class="zoom_in"></div> 
    <div class="zoom_out"></div>
</div>

<div class = 'content'>
<svg {width} {height} viewBox="0 0 {width} {height}">
    <g stroke="black" stroke-width="0.5" transform="translate(270, 100)" class = "layer" id = 'Row1'>
        <text transform="translate(100, 50)" font-size="75">{firstRow['Stat']}</text>
        <text font-size="25" transform="translate(0, 90)"> Description: {firstRow['Data_descipt']}</text>
    </g>
    <g stroke="black" stroke-width="0.5" transform="translate(30,40)" class = "layer" id = 'Row2'>
        <g transform="translate(30, 0)">
            let first = 1;
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
    <g stroke="black" stroke-width="0.5" class = "layer" id = 'Row3' transform="translate(100,0)">
        <g transform="translate(30, 40)" font-size="20">
            {#each iterations5 as i, indexh}
                {#each iterations6 as j, index}
                    <!-- <text fill="blue" x={index * spacingwidth} y={indexh * spacingheight}>{secondRow['Stat']}</text> -->
                    {#if i === 1 && j === 1}
                        <text id = "scoping"fill="orange" x={index * spacingwidth} y={indexh * spacingheight}>{secondRow['Stat']}</text>
                    {:else}
                        <text fill="blue" x={index * spacingwidth} y={indexh * spacingheight}>{secondRow['Stat']}</text>
                    {/if}

                {/each}
            {/each}
        </g>
        <g >
            <text font-size="50" transform="translate(400, 150)"> = </text>
            <g>
            <text font-size="40" transform="translate(450, 150)" fill="brown"> 3K people</text>
            <rect x=445 y=110 width=190 height=55 fill={isHovered ? 'blue' : 'pink'} on:mouseover={handleMouseOver} on:mouseout={handleMouseOut} on:mousemove={updateTooltipPosition} on:focus={handleMouseOver} on:blur={handleMouseOut} opacity = 0.2 role="presentation"/>
            </g>
        </g>
        <text font-size="25" transform="translate(-80, 285)"> Description: {thirdRow['Data_descipt']}</text>
    </g>
    <g stroke="black" stroke-width="0.5" class = "layer" id = 'Row4' transform="translate(100,10)">
        <g transform="translate(10, 50)" font-size="25">
            {#each iterations4 as i, indexh}
                {#each iterations6 as j, index}
                    {#if i === 1 && j ===1}
                        <text id = "scoping" fill="blue" x={index * 65} y={indexh * spacingheight}>{thirdRow['Stat']}</text>
                    {:else}
                        <text fill="brown" x={index * 65} y={indexh * spacingheight}>{thirdRow['Stat']}</text>
                    {/if}
                {/each}
            {/each}
        </g>
        <g>
            <text font-size="50" transform="translate(400, 130)"> = </text>
            <g>
                <text font-size="40" transform="translate(450, 130)" fill="green"> 70K people</text>
                <rect x=445 y=90 width=210 height=55 fill={isHovered ? 'blue' : 'pink'} on:mouseover={handleMouseOver} on:mouseout={handleMouseOut} on:mousemove={updateTooltipPosition} on:focus={handleMouseOver} on:blur={handleMouseOut} opacity = 0.2 role="presentation"/>
            </g>
        </g>
        <text font-size="25" transform="translate(0, 240)"> Description: {forthRow['Data_descipt']}</text>
    </g>
    <g stroke="black" stroke-width="0.5" class = "layer" id = 'Row5' transform="translate(80,10)">
        <g transform="translate(10, 50)" font-size="25">
            {#each iterations4 as i, indexh}
                {#each iterations5 as j, index}
                    {#if i === 1 && j===1}
                        <text id = "scoping" fill="rgba(245, 40, 145, 0.8)" x={index * 80} y={indexh * spacingheight}>{forthRow['Stat']}</text>
                    {:else}
                        <text fill="green" x={index * 80} y={indexh * spacingheight}>{forthRow['Stat']}</text>
                    {/if}
                {/each}
            {/each}
        </g>
        <g>
            <text font-size="50" transform="translate(410, 130)"> = </text>
            <g>
                <text font-size="40" transform="translate(460, 130)" fill="red"> 1.3M  people</text>
                <rect x=455 y=90 width=235 height=55 fill={isHovered ? 'blue' : 'pink'} on:mouseover={handleMouseOver} on:mouseout={handleMouseOut} on:mousemove={updateTooltipPosition} on:focus={handleMouseOver} on:blur={handleMouseOut} opacity = 0.2 role="presentation"/>
            </g>    
        </g>
        <text font-size="25" transform="translate(10, 240)"> Description: {fifthRow['Data_descipt']}</text>
    </g>

    {#if isHovered && page_on === 3}
        <g transform="translate(600, 220)">
            <!-- Tooltip box -->
            <rect x="0" y="-45" width="190" height="90" fill="lightyellow" stroke="yellow" />
            <!-- Text inside tooltip -->
            <text x="35" y="-15" font-size="18" fill="black">Equivalates to...</text>
            <text x="5" y="10" font-size="14" fill="black">30 rooms of DSC 106 student </text>
            <text x="30" y="25" font-size="14" fill="black">watching the demo!!</text>
        </g>
    {/if}
    {#if isHovered && page_on === 4}
        <g transform="translate(600, 220)">
            <!-- Tooltip box -->
            <rect x="0" y="-45" width="190" height="80" fill="lightyellow" stroke="yellow" />
            <!-- Text inside tooltip -->
            <text x="40" y="-25" font-size="18" fill="black">Equivalates to...</text>
            <text x="20" y="-5" font-size="14" fill="black">24 twitch streemers with 3000 daily views</text>
            <text x="20" y="10" font-size="14" fill="black">700 rooms of DSC 106 student watching the demo!!</text>
        </g>
    {/if}
    {#if isHovered && page_on === 5}
        <g transform="translate(600, 220)">
            <!-- Tooltip box -->
            <rect x="0" y="-45" width="190" height="90" fill="lightyellow" stroke="yellow" />
            <!-- Text inside tooltip -->
            <text x="40" y="-25" font-size="18" fill="black">Equivalates to...</text>
            <text x="20" y="-5" font-size="14" fill="black">20 Sofi Stadium</text>
            <text x="20" y="10" font-size="14" fill="black">440 twitch streemers with 3000 daily views</text>
            <text x="20" y="25" font-size="14" fill="black">13000 rooms of DSC 106 student watching the demo!!</text>
        </g>
    {/if}
</svg>
</div>


<style>
.buttons {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 80px; 
}

.zoom_in{
    width: 150px; 
    height: 70px;
    margin-right: 50px; 
    justify-content: center; 
    align-items: center; 
    display: flex; 

    
}
.zoom_out {
    width: 150px; 
    height: 70px;
    margin-right: 14px; 
    display: flex; 
    justify-content: center; 
    align-items: center; 
}

#Row2,
#Row3,
#Row4,
#Row5{
    display: none;
}



</style>