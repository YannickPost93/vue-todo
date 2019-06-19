<template>
  <div class="hello">
    <div class="holder">
      <transition name='alert-in'>
        <p class="alert" v-if="errors.has('todo')">{{ errors.first('todo') }}</p>
      </transition>
    
      <form @submit.prevent="addToDo">
        <input type="text" placeholder="Create a new thing to do.." v-model="todo" v-validate="'min:2'" name="todo"/>
      <!-- <input type="checkbox" id="checkbox" v-model="checked">Important! -->
     
      </form>
      <p>These are the things you'll have to do</p>
      <ul>
        <li v-for="(data, index) in todos" :key='index'>{{ data.todo }}</li>
      </ul> 

      <p v-if="todos.length == 0">You're free!</p>
      <p v-else>Get your shit together and finish some stuff!</p>

    </div>
  </div>
</template>

<script>
export default {
  name: 'ToDo',
  data() {
    
    return {
      // checked: false,
      todo: '',
      todos: [
        { "todo": "Specialize me"},
        { "todo": "Sector verdieping"}
      ]
    }
  },
  methods: {
    addToDo() {
      this.$validator.validateAll().then((result) => {
        if(result){
          this.todos.push({todo: this.todo}),
          this.todo = '';
        } else {
          console.log('notValid');
        }
      });
 
      // console.log('Checkbox is '+this.checked);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style src="./css/ToDo.css" scoped></style>
