<template>
  <div id="app"> 
    <Searcher/>
  </div>
</template>

<script> 
import Searcher from './components/Searcher.vue'

export default {
  name: 'App',
  components: {
    Searcher
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50; 
  height: 100%;
}
html ,body{
  padding: 0;
  margin: 0;
  height: 100%;

}

h1 {
  margin: 0;
}

</style>
