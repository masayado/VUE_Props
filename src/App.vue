<template>
  <div id="app" class="container">
    <h1>{{title}}</h1>
    {{subtitle}}
    <input type="text" placeholder="Ingresa una nueva tarea" v-model="tareas">
    <div><button class="crear_button" @click="agregar_tarea">Crear</button></div>
    <br>
    <h3>{{subtitle}}</h3>
        <ol>
        <li v-for="tareas in tareas2">
        {{tareas}}
        <delete-component></delete-component>
        </li>
        </ol>
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
        agregar_tarea:function(tareas, index){
            if(this.tareas != ""){
                this.tareas2.push(this.tareas)
                this.tareas="";
            }
        },
        borrar_tarea:function(tareas){
            const tareasIndex = this.tareas2.indexOf(tareas);
            this.tareas2.splice(tareasIndex, 1);
        }
    },
    components:{
        'delete-component':DeleteComponent,
    },
  }
</script>

<style>

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
    }

ol{
    padding-left:25px;
    padding-right:25px;
    }

p{
    text-align: center;
    }

h1{
    text-align:center;
    }

</style>