<template>
  <div id="app">
    <ToDo msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import ToDo from './components/ToDo.vue'

export default {
  name: 'app',
  components: {
    ToDo
  }
}
</script>

<style src="./components/css/normalize.css"></style>
<style>
@import url('https://fonts.googleapis.com/css?family=Montserrat:400,700');

body {
  background-color: #EEEEEE;
  font-family: 'Montserrat', sans-serif;
  display: grid;
  grid-template-rows: auto;
  justify-items: center;
  align-items: center;
}
body, html {
  margin: 0;
  height: 100%;
}
#app {
    width: 50%;
}
</style>
