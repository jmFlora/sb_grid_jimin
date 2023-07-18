<template>
    <div>
        <select v-model="sortOption">
            <option value="asc">오름차순</option>
            <option value="desc">내림차순</option>
        </select>
        <button @click="optionClick">sortColumn</button>
      <div class="gridForm">
          <SBGrid
                  id="dataGrid"
                  style="width: 990px; height: 300px"
                  ref="grid"
                  :data="sumData"
                  :columns="totalColumn"
                  :gridattr="{
                      backcoloralternate: '#efefef',
                      rowheigt: '26',
                      rowheader: 'seq',
                      selectmode:'free',
                      saveorgdata: true,
                      useinitsorting: true,
                      selectcellfocus: true,
                      extendcol: 2
                       // paging:{'type':'all', 'count': 5, 'size':12},
                     }"
          ></SBGrid>
      </div>
    </div>
</template>
<script>
import SBGrid from './SBGrid.vue' // SBGrid 컴포넌트를 불러옵니다.
import dataJson from "../../json/dataJson.json";
export default{
    data: function() {
        return {
            sumData : dataJson.gridJson,
            totalColumn: dataJson.grid1columns,
            sortOption:"asc",
        }
    },
    components: {
        SBGrid // 불러온 SBGrid 컴포넌트를 TotalGrid.vue에서 사용할 수 있도록 등록합니다.
    },
    methods:{
        optionClick(){
          const gridList = this.$refs.grid.gridObject
            if(gridList.getCol()<0){
                alert("정렬할 열을 선택해 주세요")
            }else{
                gridList.sortColumn(gridList.getCol(), this.sortOption)
                gridList.sortingIcon();
            }
      }
    }
}
</script>