<template>
<div class="container">
  <div id="app">
    <h1>{{title}}</h1>
    {{subtitle}}
    <input type="text" placeholder="Ingresa una nueva tarea" v-model="tareas">
    <div><button @click="agregar_tarea">Crear</button></div>
    <br>
    <h3>{{subtitle}}</h3>
        <ol>
        <li v-for="tareas in tareas2">
        {{tareas}}
        <delete-component></delete-component>
        </li>
        </ol>
    <delete-component></delete-component>
  </div>
</div>
</template>

<script>
import DeleteComponent from "./components/Delete.vue"
  export default {
    name:'app-component',
    //props: {},
    data: function(){
      return {
        title: 'To-Do List',
        subtitle: 'Lista de tareas',
        paragraph: "Ingresa la tarea",
        tareas:"",
        tareas2:[],
      }
    },
    //computed:{},
    methods:{
        agregar_tarea:function(){
            if(this.tareas != ""){
                this.tareas2.push(this.tareas)
                this.tareas="";
            }
        }
    },
    components:{
        'delete-component':DeleteComponent,
    },
  }
</script>

<style scoped>
  #app {
    *{
    margin:0 auto;
    padding:0;
    box-sizing: border-box;
    font-family: 'Helvetica', sans-serif;
    }

.container{
    position: relative;
    top:100px;
    margin:auto;
    width: 30%;
    background-color: #f9fafb;
    padding:25px;
    line-height: 1.6;
    display: flex;
    justify-content: center;
    }

ol{
    padding-left:25px;
    padding-right:25px;
    }

p{
    text-align: center;
    }

input{
    padding:10px;
    width:300px;
    margin:5px;
    }

button{
    color: #f9fafb;
    padding:10px;
    clear: both;
    width:300px;
    margin:5px;
    background-color: #343a40;
    border-style: none;
    cursor: pointer;
    border-radius: 3px;
    }

button:hover{
    background-color: #191c1e;
    }

h1{
    text-align:center;
    }

}
</style>