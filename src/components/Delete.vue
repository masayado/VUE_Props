<template>
    <i class="fas fa-times-circle" id="app" @click="borrar(id)"></i>
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
    //data: function(){
       // return{}
    //},
    //computed: {},
    methods:{
        borrar:function(id){
            //alert(id);
           this.$emit("borrar", {id:id})
        },
    }
    //componentes:{},
}
</script>

<style scoped>

</style>