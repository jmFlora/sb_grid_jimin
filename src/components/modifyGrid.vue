<template>
    <div class="modifyForm">
      <h3>수정</h3>
        <div>
            <label>소속</label>
            <select v-model="divide">
                <option value="0">소속을 입력해주세요</option>
                <option value="FE팀">FE팀</option>
                <option value="BE팀">BE팀</option>
                <option value="DX팀">DX팀</option>
            </select>
        </div>
        <div>
            <label>성명</label>
            <input type="text" v-model="name">
        </div>
        <div>
            <label>전화번호</label>
            <input type="text" v-model="phone">
        </div>
        <div>
            <label>직급</label>
            <select v-model="rank">
                <option value="팀장">팀장</option>
                <option value="파트장">파트장</option>
                <option value="프로">프로</option>
            </select>
        </div>
        <div>
            <label>생년월일</label>
            <input type="date" v-model="birth">
        </div>
        <div>
            <label>입사월일</label>
            <input type="date" v-model="startDate">
        </div>
        <div>
            <label>나이</label>
            <input type="number" v-model="age">
        </div>
        <!--        <div>-->
        <!--            <label>5월</label>-->
        <!--            <input type="number" v-model="may">-->
        <!--        </div>-->
        <div>
            <button @click="setModiRow">폼입력하여 수정</button>
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
            divide:"0",
            name:"",
            phone:"",
            rank:"",
            birth:"",
            startDate:"",
            age:"",

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
                this.divide = this.gridJson[nRow - 1].divide;
                this.name = this.gridJson[nRow - 1].name;
                this.phone = this.gridJson[nRow - 1].phone;
                this.birth = this.gridJson[nRow - 1].birth;
                this.startDate = this.gridJson[nRow - 1].startDate;
                this.rank = this.gridJson[nRow - 1].rank;
                this.age = this.gridJson[nRow - 1].age;
            }
        },
        setModiRow(){
            const gridList  = window._SBGrid.getGrid("dataGrid");
            const nRow = gridList.getRow();
            const data ={
                "divide": this.divide,
                "name": this.name,
                "phone": this.phone,
                "birth": this.birth,
                "startDate": this.startDate,
                "rank": this.rank,
                "age": this.age,
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