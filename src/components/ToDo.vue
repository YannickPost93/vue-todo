<template>
  <div class="hello">
    <div class="holder">
      <transition name="alert-in" enter-active-class="animated flipInX" leave-active-class="animated flipOutX">
          <p class="alert" v-if="errors.has('todo')">{{ errors.first('todo') }}</p>
      </transition>
    
      <form @submit.prevent="addToDo">
        
        
        <input type="text" placeholder="Create a new thing to do.." v-model="todo" v-validate="'min:2'" name="todo"/>
      
     
      
      </form>
      <p>These are the things you'll have to do</p>
      <ul>
        <transition-group name="list" enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutDown">
          <li v-for="(data, index) in todos" :key='index'>
            {{ data.todo }}
            <i class="fa fa-minus-circle" v-on:click="remove(index)"></i>
          </li>
        </transition-group>
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
          // console.log('notValid');
        }
      });
 
      // console.log('Checkbox is '+this.checked);
    },
    remove(id) {
      this.todos.splice(id,1);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style src="./css/ToDo.css" scoped></style>
