<template>
  <div id="app">
    {{ message }}
  </div>
</template>

<script>
  export default {
    data() {
      return {
        message: 'To-Do List',
      };
    }
  }
</script>

<style scoped>
  #app {
    font-size: 25px;
    font-family: "Calibri", sans-serif;
  }
</style>