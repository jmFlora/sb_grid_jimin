<template>
  <div class="gridForm">
      <SBGrid
              id="dataGrid"
              style="width: 100%; height: 300px"
              ref="grid"
              :data="sumData"
              :columns="totalColumn"
              :gridattr="{
                  backcoloralternate: '#efefef',
                  rowheihgt: '26',
                  rowheader: 'seq',
                  selectmode:'free',
                  saveorgdata: true
                 }"
      ></SBGrid>
  </div>
</template>
<script>
import SBGrid from './SBGrid.vue' // SBGrid 컴포넌트를 불러옵니다.
import dataJson from "../../json/dataJson.json";
export default{
    data: function() {
        return {
            sumData : dataJson.gridJson,
            totalColumn: dataJson.grid1columns
        }
    },
    components: {
        SBGrid // 불러온 SBGrid 컴포넌트를 TotalGrid.vue에서 사용할 수 있도록 등록합니다.
    },
}
</script>