<template>

  <div id="app" class="container">

        <h1>{{title}}</h1>

        <div class="form">
        <input type="text" v-model="tareas" placeholder="Ingresa una nueva tarea" @keyup.enter="agregar_tarea">
        <button @click="agregar_tarea" class="crear_button">Agregar</button>
        </div>

        <h3>{{subtitle}}</h3>
        <div class="lista">
            <ol>
            <li v-for="(tareas, index) in tareas2"
            :tareas="tareas"
            :index="index"
            :key="tareas.id"
            >

            {{tareas}}

            <delete-component :id="index" @borrar="borrar_tarea"></delete-component>
            
            </li>
            </ol>
        </div>
  </div>
  
</template>

<script>
import DeleteComponent from "./components/Delete.vue"
  export default {
    name:'app-component',
    //props: {},
    data(){
      return {
        title: 'To-Do List',
        subtitle: 'Lista de tareas',
        paragraph: "Ingresa la tarea",
        tareas2:[],
        tareas:"",
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
        borrar_tarea:function(e){
           // alert("Estoy borrando la tarea")
            let id = e.id;
            let tareasIndex = this.tareas2.findIndex((tareas)=>tareas.id === id);
            this.tareas2.splice(id,1);
        }
    },
    components:{
        'delete-component':DeleteComponent,
    },
  }
</script>

<style scoped>

.container{
    margin:0 auto;
    padding:25px;
    box-sizing: border-box;
    font-family: 'Helvetica', sans-serif;
    position: relative;
    top:80px;
    margin:auto;
    width: 40%;
    background-color: #f9fafb;
    line-height: 1.6;
    display:flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    }

h1, h3{
    text-align: center;
}

ol{
    padding-left:25px;
    padding-right:25px;
    }

.form{
    display: flex;
}

input{
    padding:10px;
    width:230px;
    margin:5px;
}

.crear_button{
    color: #f9fafb;
    padding:10px;
    width:70px;
    margin:5px;
    background-color: #343a40;
    border-style: none;
    cursor: pointer;
    border-radius: 3px;
    }

button:hover{
    background-color: #191c1e;
    }

.lista{
    display:flex;
    justify-content: space-between;
}

</style>