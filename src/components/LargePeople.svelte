<script>
export let large_people_data;

import * as d3 from 'd3';

const width = 928;
const height = 1500;

export const firstRow = large_people_data[0]
export const secondRow = large_people_data[1]
export const thirdRow = large_people_data[2]
export const forthRow = large_people_data[3]
export const fifthRow = large_people_data[4]
export const sixthRow = large_people_data[5]
export const seventhRow = large_people_data[6]

const iterations2 = Array.from({ length: 2 }, (_, index) => index + 1);
const iterations3 = Array.from({ length: 3 }, (_, index) => index + 1);
const iterations4 = Array.from({ length: 4 }, (_, index) => index + 1);
const iterations5 = Array.from({ length: 5 }, (_, index) => index + 1);
const iterations6 = Array.from({ length: 6 }, (_, index) => index + 1);
const iterations10 = Array.from({ length: 10 }, (_, index) => index + 1);

let spacingwidth = 50
let spacingwidth_1 = 40
let spacingwidth_2 = 70
let spacingheight  = 20
console.log(firstRow['Data_descipt'])




</script>


<svg {width} {height} viewBox="0 0 {width} {height}">
    <g id = 'Row1'stroke="black" stroke-width="0.5" transform="translate(0, 50)">
        <text font-size="50">{firstRow['Stat']} people</text>
        <text transform="translate(0, 30)"> Description: {firstRow['Data_descipt']}</text>
    </g>
    <g id = 'Row2'stroke="black" stroke-width="0.5" transform="translate(0,130)">
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
        <text transform="translate(0, 200)"> Description: {secondRow['Data_descipt']}</text>
    </g>
    <g id = 'Row3'stroke="black" stroke-width="0.5" transform="translate(0, 390)">
        <g>
            {#each iterations5 as i, indexh}
                {#each iterations6 as j, index}
                    <text x={index * spacingwidth} y={indexh * spacingheight}>{secondRow['Stat']}</text>
                {/each}
            {/each}
        </g>
        <g>
            <text font-size="50" transform="translate(450, 50)"> = 3K people</text>
        </g>
        <text transform="translate(0, 100)"> Description: {thirdRow['Data_descipt']}</text>
    </g>
    <g id = 'Row4'stroke="black" stroke-width="0.5" transform="translate(0, 550)">
        <g>
            {#each iterations4 as i, indexh}
                {#each iterations6 as j, index}
                    <text x={index * spacingwidth} y={indexh * spacingheight}>{thirdRow['Stat']}</text>
                {/each}
            {/each}
        </g>
        <g>
            <text font-size="50" transform="translate(450, 50)"> = 70K people</text>
        </g>
        <text transform="translate(0, 80)"> Description: {forthRow['Data_descipt']}</text>
    </g>
    <g id = 'Row5'stroke="black" stroke-width="0.5" transform="translate(0, 700)">
        <g>
            {#each iterations3 as i, indexh}
                {#each iterations5 as j, index}
                    <text x={index * spacingwidth} y={indexh * spacingheight}>{forthRow['Stat']}</text>
                {/each}
            {/each}
        </g>
        <g>
            <text font-size="50" transform="translate(450, 30)"> = 1M  people</text>
        </g>
        <text transform="translate(0, 60)"> Description: {fifthRow['Data_descipt']}</text>
    </g>
    <g id = 'Row6'stroke="black" stroke-width="0.5" transform="translate(0, 800)">
        <g>
            {#each iterations4 as i, indexh}
                {#each iterations6 as j, index}
                    <text x={index * spacingwidth_2} y={indexh * spacingheight}>{fifthRow['Stat']}</text>
                {/each}
            {/each}
        </g>
        <g>
            <text font-size="50" transform="translate(450, 30)"> = 24M  people</text>
        </g>
        <text transform="translate(0, 80)"> Description: {sixthRow['Data_descipt']}</text>
      
    </g>
    <g id = 'Row7'stroke="black" stroke-width="0.5" transform="translate(0, 930)">
        <g>
            {#each iterations2 as i, indexh}
                {#each iterations5 as j, index}
                    <text x={index * spacingwidth_2} y={indexh * spacingheight}>{sixthRow['Stat']}</text>
                {/each}
            {/each}
        </g>
        <g>
            <text font-size="50" transform="translate(450, 30)"> = 240M  people</text>
        </g>
        <text transform="translate(0, 50)"> Description: {seventhRow['Data_descipt']}</text>
    </g>
</svg>








<style>


</style>