<template>
  <body>
    <div id="app">
      <Body/>
    </div>
  </body>
</template>

<script>
  import Body from './components/Body.vue'
  
  export default {
    components: {
      Body
    }
     
  }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  text-align: center;
  color: black;
}
body{
  text-align: center;
  background-image: url("./assets/backgroundimg.jpg");
  background-size: cover; 
}
</style>