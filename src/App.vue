<template>
    <div>
        <IdevelList></IdevelList>
        <div class="button-container">
            <button @click="editForm" style="margin-right: 10px" >등록</button>
            <button @click="editForm">수정</button>
        </div>
        <insert-grid v-if="regi"></insert-grid>
        <modify-grid v-else></modify-grid>

    </div>
    <hr style="margin-top: 30px; margin-bottom: 30px">
    <div>
        <TotalGrid></TotalGrid>
    </div>
</template>

<script>
import TotalGrid from "@/components/TotalGrid.vue";
import InsertGrid from "@/components/InsertGrid.vue";
import ModifyGrid from "@/components/modifyGrid.vue";
import IdevelList from "@/components/IdevelList.vue";

export default {
    name: 'App',
    components: {
        IdevelList,
        ModifyGrid,
        InsertGrid,
        TotalGrid,
    },
    data(){
        return{
            regi:true,
        }
    },
    computed:{
      text(){
          return this.regi ? "수정하기" : "등록하기"
      }
    },
    methods:{
        editForm(){
            this.regi = !this.regi
        }
    }
}
</script>

<style>
.button-container {
    text-align: center;
    margin-top: 20px;
    margin-bottom: 30px;
}

.button-container button {
    background-color: #4CAF50;
    color: white;
    padding: 10px 16px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

.button-container button:hover {
    background-color: #45a049;
}
</style>
