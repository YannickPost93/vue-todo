<template>
  <div class="hello">
    <div class="holder">
      <ul>
        <li v-for="(data, index) in todos" :key='index'>{{ index }}. {{ data.todo }}</li>
      </ul> 

      <p v-if="todos.length == 0">You're free!</p>
      <p v-else>Get your shit together and finish some stuff!</p>

      <div v-bind:class="{ alert: !showAlert }"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ToDo',
  data() {
    return {
      todos: [
        { "todo": "Specialize me"},
        { "todo": "Sector verdieping"}
      ],
      showAlert: true
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style src="./css/ToDo.css" scoped></style>
