<template>
  <div id="app">
    <appBody/>
  </div>
</template>

<script>
  import appBody from './components/Body.vue';
  
  export default {
    components: {appBody}
  }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>