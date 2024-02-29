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

const iterations4 = Array.from({ length: 4 }, (_, index) => index + 1);
const iterations5 = Array.from({ length: 5 }, (_, index) => index + 1);
const iterations6 = Array.from({ length: 6 }, (_, index) => index + 1);
const iterations10 = Array.from({ length: 10 }, (_, index) => index + 1);

let spacingwidth = 50
let spacingwidth_1 = 40
let spacingheight  = 20

let page_on = 1;



</script>


<svg {width} {height} viewBox="0 0 {width} {height}" id = 'Row1'>
    <g stroke="black" stroke-width="0.5" transform="translate(0, 100)">
        <text transform="translate(100, 0)" font-size="75">{firstRow['Stat']}</text>
        <text transform="translate(0, 30)"> Description: {firstRow['Data_descipt']}</text>
    </g>
</svg>
<svg {width} {height} viewBox="0 0 {width} {height}" id = 'Row2'>
    <g stroke="black" stroke-width="0.5" transform="translate(0,100)">
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
</svg>
<svg {width} {height} viewBox="0 0 {width} {height}" id = 'Row3'>
    <g id = 'Row3'stroke="black" stroke-width="0.5" transform="translate(0, 100)">
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
</svg>
<svg {width} {height} viewBox="0 0 {width} {height}" id = 'Row4'>
    <g stroke="black" stroke-width="0.5" transform="translate(0, 100)">
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
</svg>
<svg {width} {height} viewBox="0 0 {width} {height}" id = 'Row5'>
    <g stroke="black" stroke-width="0.5" transform="translate(0, 100)">
        <g>
            {#each iterations4 as i, indexh}
                {#each iterations5 as j, index}
                    <text x={index * spacingwidth} y={indexh * spacingheight}>{forthRow['Stat']}</text>
                {/each}
            {/each}
        </g>
        <g>
            <text font-size="50" transform="translate(450, 30)"> = 1.3M  people</text>
        </g>
        <text transform="translate(0, 90)"> Description: {fifthRow['Data_descipt']}</text>
    </g>
</svg>

<style>


</style>