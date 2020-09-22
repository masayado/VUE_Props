<template>
    <button @click="borrar(id)">Borrar</button>
</template>

<script>
export default {
    name: 'delete-component',
    props: {
        id:{
            type:Number,
            required:true,
        },
    },
    data: function(){
        return{}
    },
    //computed: {},
    methods:{
        borrar(id){
            //alert("borrando");
            this.$emit("borrar",{id:id})
        },
    },
    //componentes:{},
}
</script>

<style scoped>

button{
    color: #f9fafb;
    padding:8px;
    margin:5px;
    background-color: #343a40;
    border-style: none;
    cursor: pointer;
    border-radius: 3px;
    }

</style>