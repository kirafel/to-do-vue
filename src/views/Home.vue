<template>
  <div id="app">
    <img alt="Vue logo" src="../assets/logo.png" width="100px" height="100px">
    <h1><u>Vue.js Todo List</u></h1>
    <AddToDo @addTodo="addToDoArray"/>
    <ToDo :todos="listToDos" @delete-item="deleteFromArray"/>
  </div>
</template>

<script>
import ToDo from '../components/ToDo.vue'
import AddToDo from '../components/AddToDo.vue'


export default {
  name: 'Home',
  components: {
    ToDo,
    AddToDo
  },
  data() {
    return {
      listToDos : [
        {
          id : 1,
          title : 'Todo One',
          completed : false
        },
        {
          id : 2,
          title : 'Todo Two',
          completed : true
        },
        {
          id : 3,
          title : 'Todo Three',
          completed : false
        },
        {
          id : 4,
          title : 'Todo Four',
          completed : true
        },
        {
          id : 5,
          title : 'Todo Five',
          completed : false
        }
      ]
    }
  },
  methods : {
    deleteFromArray : function(id) {
      this.listToDos = this.listToDos.filter((todo) => todo.id != id);
    },

    addToDoArray: function(title) {
      this.listToDos.push({id : this.listToDos.length + 1, title: title, completed: false});
    } 
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
}
</style>
