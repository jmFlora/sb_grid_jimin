<template>
    <div class="writeForm">
        <h3>등록</h3>
        <div>
            <label>구분</label>
            <select v-model="divide">
                <option value="0">구분을 입력해주세요</option>
                <option value="수입">수입</option>
                <option value="지출">지출</option>
            </select>
        </div>
        <div>
            <label>분류</label>
            <input type="text" v-model="sortChk">
        </div>
        <div>
            <label>항목</label>
            <input type="text" v-model="item">
        </div>
        <div>
            <label>1월</label>
            <input type="number" v-model="jan">
        </div>
        <div>
            <label>2월</label>
            <input type="number" v-model="feb">
        </div>
        <div>
            <label>3월</label>
            <input type="number" v-model="mar">
        </div>
        <div>
            <label>4월</label>
            <input type="number" v-model="apr">
        </div>
        <div>
            <label>5월</label>
            <input type="number" v-model="may">
        </div>
        <div>
            <label>6월</label>
            <input type="number" v-model="jun">
        </div>
        <div>
            <label>7월</label>
            <input type="number" v-model="jul">
        </div>
        <div>
            <label>8월</label>
            <input type="number" v-model="aug">
        </div>
        <div>
            <label>9월</label>
            <input type="number" v-model="sep">
        </div>
        <div>
            <label>10월</label>
            <input type="number" v-model="oct">
        </div>
        <div>
            <label>11월</label>
            <input type="number" v-model="nov">
        </div>
        <div>
            <label>12월</label>
            <input type="number" v-model="dec">
        </div>
        <div>
            <button @click="setRow">폼입력하여 등록</button>
        </div>
    </div>
</template>

<script>
import dataJson from '/json/dataJson.json'
  export default {
      data(){
          return{
              gridJson: dataJson.gridJson,
              grid1columns: dataJson.grid1columns,
              divide:"0",
              sortChk:"",
              item:"",
              jan:"",
              feb:"",
              mar:"",
              apr:"",
              may:"",
              jun:"",
              jul:"",
              aug:"",
              sep:"",
              oct:"",
              nov:"",
              dec:"",

          }
      },
      mounted() {
          this.$nextTick(function() {

          })
      },
      methods: {
          //셀만 추가
          // insertList(){
          //     const gridList  = window._SBGrid.getGrid("dataGrid");
          //     gridList.addRow();
          // },
          //입력 후 긔리드에 추가
          setRow(){
              const gridList  = window._SBGrid.getGrid("dataGrid");
              const data = {
                  "col0": this.divide,
                  "col1": this.sortChk,
                  "col2": this.item,
                  "col3": this.jan,
                  "col4": this.feb,
                  "col5": this.mar,
                  "col6": this.apr,
                  "col7": this.may,
                  "col8": this.jun,
                  "col9": this.jul,
                  "col10":this.aug ,
                  "col11":this.sep ,
                  "col12":this.oct ,
                  "col13":this.nov ,
                  "col14":this.dec ,
              };
              this.gridJson.push(data)
              gridList.addRow();
              gridList.removeRow();
          },
      }
  }
</script>

<style scoped>
</style>