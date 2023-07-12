<template>
    <div class="modifyForm">
      <h3>수정</h3>
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
        <button @click="setModiRow">수정</button>
    </div>
    </div>
</template>
<script>
import dataJson from "../../json/dataJson.json";

export default {
    data() {
        return {
            gridJson: dataJson.gridJson,
            grid1columns: dataJson.grid1columns,
            divide: "0",
            sortChk: "",
            item: "",
            jan: "",
            feb: "",
            mar: "",
            apr: "",
            may: "",
            jun: "",
            jul: "",
            aug: "",
            sep: "",
            oct: "",
            nov: "",
            dec: "",

        }
    },
    mounted() {
        this.$nextTick(function() {
            const gridList  = window._SBGrid.getGrid("dataGrid");
            gridList.bind("click", this.gridClick)

        })
    },
    methods:{
        //그리드를 클릭 하였을 때에 이밴트를 준다.
        gridClick(){
            const gridList  = window._SBGrid.getGrid("dataGrid");
            const nRow = gridList.getRow();
            if(nRow<0){
                alert("행을 선택해 주세요")
            }else {
                // 데이터 바인딩
                this.divide = this.gridJson[nRow - 1].col0;
                this.sortChk = this.gridJson[nRow - 1].col1;
                this.item = this.gridJson[nRow - 1].col2;
                this.jan = this.gridJson[nRow - 1].col3;
                this.feb = this.gridJson[nRow - 1].col4;
                this.mar = this.gridJson[nRow - 1].col5;
                this.apr = this.gridJson[nRow - 1].col6;
                this.may = this.gridJson[nRow - 1].col7;
                this.jun = this.gridJson[nRow - 1].col8;
                this.jul = this.gridJson[nRow - 1].col9;
                this.aug = this.gridJson[nRow - 1].col10;
                this.sep = this.gridJson[nRow - 1].col11;
                this.oct = this.gridJson[nRow - 1].col12;
                this.nov = this.gridJson[nRow - 1].col13;
                this.dec = this.gridJson[nRow - 1].col14;
            }
        },
        setModiRow(){
            const gridList  = window._SBGrid.getGrid("dataGrid");
            const nRow = gridList.getRow();
            const data ={
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
            }
            if(nRow <0){
                alert("행을 선택해 주세요")
            }else{
                gridList.setRowData(nRow, data);
            }
        }
    }
}
</script>
<style>
</style>