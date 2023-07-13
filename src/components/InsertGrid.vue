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
<!--        <div>-->
<!--            <label>5월</label>-->
<!--            <input type="number" v-model="may">-->
<!--        </div>-->
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
</style>