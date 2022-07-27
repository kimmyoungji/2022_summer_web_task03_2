<script lang="ts">
    // export let h:number;
    export let yLegend:number;
</script>

<div class="graphBg" >
    <p>{yLegend}</p>
</div>


<style lang="scss">
    .graphBg{
        //box style
        height:49px;
        width: 900px;
        border-bottom: solid black 1px;

        //contents style
        display: flex;
        flex-flow: column-reverse wrap;
        justify-content: flex-end;
    }

    .graphBg p{
        display:flex;
        justify-self: flex-end;
        position: relative;
        top: 13px;
        left:3px;
    }
</style>