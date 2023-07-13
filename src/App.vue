<template>

    <TotalGrid></TotalGrid>
    <div>
        <button @click="editForm">{{text}}</button>
    </div>
    <insert-grid v-if="regi"></insert-grid>
    <modify-grid v-else></modify-grid>
</template>

<script>
import TotalGrid from "@/components/TotalGrid.vue";
import InsertGrid from "@/components/InsertGrid.vue";
import ModifyGrid from "@/components/modifyGrid.vue";

export default {
    name: 'App',
    components: {
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
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    /*text-align: center;*/
    color: #2c3e50;
    margin-top: 60px;
}
</style>
