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
  background-color: White;
  /*background-image: url("https://cdn.pixabay.com/photo/2016/12/02/02/10/idea-1876659_960_720.jpg");
  background-repeat: no-repeat;
  background-size: 1299px 679px;*/
}
</style>