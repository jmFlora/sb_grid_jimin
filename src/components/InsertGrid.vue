<template>
    <div class="writeForm">
        <h3>등록</h3>
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
                  "divide": this.divide,
                  "name": this.name,
                  "phone": this.phone,
                  "birth": this.birth,
                  "startDate": this.startDate,
                  "rank": this.rank,
                  "age": this.age,
              };
              this.gridJson.push(data);
              gridList.removeRowStatus(15)
              // gridList.addRow();
              // gridList.removeRow();
          },
      }
  }
</script>

<style scoped>
.writeForm {
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 4px;
    background-color: #f9f9f9;
}

.writeForm h3 {
    margin-top: 0;
}

.writeForm label {
    display: block;
    margin-bottom: 5px;
}

.writeForm select,
.writeForm input[type="text"],
.writeForm input[type="date"],
.writeForm input[type="number"] {
    width: 100%;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
    margin-bottom: 10px;
}

.writeForm button {
    background-color: #4CAF50;
    color: white;
    padding: 10px 16px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

.writeForm button:hover {
    background-color: #45a049;
}
</style>