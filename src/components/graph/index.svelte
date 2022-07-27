<script lang="ts">
    export let text:string;
    export let gHeight:number=0;
</script>

<!-- <div class="graph" height={gHeight}>
    hello I am graph {text}
</div> -->

<div class="graph" style="height:{gHeight}px">{text}</div>

<style lang="scss">
    .graph {
        background-color: cornflowerblue;
        width:50px;
        height : var(gHeight);
    }
</style>