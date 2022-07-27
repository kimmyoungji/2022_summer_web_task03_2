<script lang="ts">
    import { Graph } from "@src/components/graph";
    import { GraphBg } from "@src/components/graphBackground";
    let dataList:number[] = [1902,2000,392,400,770];
    let heightList:number[] = getHeight(dataList);
    let ScaleList: number[] = getScale(dataList);

    // get Height of graph
    function getHeight(datas:number[]):number[]{
        let resultHeights:number[]=[];
        //getMax
        let maxIndex:number = 0;
        for(let i=0 ; i < datas.length ; i++){
            if(datas[i] >= datas[maxIndex])
                maxIndex = i;
        }
        //get Min
        let minIndex:number = 0;
        for(let i=0 ; i < datas.length ; i++){
            if(datas[i]<datas[maxIndex])
                minIndex = i;
        }
        //getHeight of graph 
        let adjustH:number = (500/datas[maxIndex]);
        for(let i=0 ; i < datas.length ; i++){
            resultHeights[i] = datas[i]*adjustH;
        }
        console.log(resultHeights);
        return resultHeights;
    }

    // get scale of graph
    function getScale(datas:number[]):number[]{
        let resultScale:number[] = [];

        //getMax
        let maxIndex:number = 0;
        for(let i=0 ; i < datas.length ; i++){
            if(datas[i] >= datas[maxIndex])
                maxIndex = i;
        }

        let ceilMax:number= Math.round(datas[maxIndex]);
        let gap:number = ceilMax/10;
        for(let i = 0 ; i < 10 ; i++){
            resultScale[i] = i*gap;
        }
        
        console.log(resultScale);

        return resultScale;
    } 
</script>

<div class="displayScreen">
    <div class="GraphFrame">
        <div class="Graphs">
            {#each heightList as height }
                <Graph gHeight={height} text={`data`}/>
            {/each}
        </div>
        <div class="GraphBgs">
            {#each ScaleList as scale  }
                <GraphBg yLegend={scale}></GraphBg>
            {/each}
            
        </div>
    </div>
</div>
    
<style>
    .displayScreen{
        /* box style */
        width: 100%;
        height: 100%;

        /* content style */
        display: flex;
        justify-content: center;
        align-content: center;
    }

    .GraphFrame{
        /* box style */
        width: 900px;
        height: 500px;
        position: static;
        margin: 100px 100px 100px 100px;
        background-color: aquamarine;
        
        /* contents style */
        display: flex;
        flex-flow: row nowrap;
        justify-content: center;
        align-content: flex-end;
    }

    .Graphs{
        width: inherit;
        height: inherit;
        z-index: 2;
        position: absolute;

        /* contents style */
        display: flex;
        flex-flow: row nowrap;
        justify-content: space-around;
        align-items: flex-end;
    }

    .GraphBgs{
        /* contents style */
        width: inherit;
        height: inherit;
        z-index: 1;
        position: relative;

        /* contents style */
        display: flex;
        flex-flow: column-reverse nowrap;
        justify-items: center;
        align-items: center;        
    }
    
    /* align-items 와 align-content: 의 차이: */
        /* align-items는 counter-axis 방향을 기준으로 아이템들을 한줄로 맞추고(정렬) */
        /* align-items는 counter-axis 방향을 기준으로 콘텐츠를 한 덩러리(한 줄)로보고, 한줄로 맞춘다(정렬)*/
        /* 일러스트레이터에 비유하여 설명하자면, align-items는 분리된 여러개의 item을 선택하여 정렬 해주는 것이고
        align-content는 분리된 여러개의 item들을 그룹핑한 뒤에 정렬해주는 것과 유사하다. 이건 완벽한 설명은 아니다 */
        /* 다시, align-items는 아이템이 들어있는 line을 정렬해주고, align-content는 아이템들이 들어있는 block을 정렬해준다. */
        /* 위의 문장에 대한 부가 설명: items를 담는 box의 display가 flex 일경우, item들이 한줄에 다 담기지 못할 겨우 다음 줄로 넘어가게 
        된다. 그래서, align-items을 해주면, line을 정렬 해준다는 표현을 한 것이다. 예를 들어, display: flex 이고, flex-dirextion: row wrap
        인 화면 크기의 박스안의 아이템들이 한줄이 넘어가서 두 줄이 된경우, align-items:center를 해주면 
        한줄에 해당하는 items들이 한줄로 가운데 정렬되고, 나머지 한줄도 그 줄을 이루는 아이템끼리 가운데 정렬 된다. 
        그리고, 각 두 줄도 화면의 세로축(중심축이 가로축이므로)의 높이를 기준으로 가운데 정렬된다(세로축 높이를 균일하게 분할하는 지점에
        각 두줄이 위치하게 된다.)*/
        /* 정렬: 행또는 열을 균일하게 맞춘다. */
</style>



