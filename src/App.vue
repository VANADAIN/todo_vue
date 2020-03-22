<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo"/>
    <todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import todos from "./components/todos"
import AddTodo from "./components/AddTodo"
import Header from "./components/layout/Header"

export default {
  name: 'app',
  components: {
    Header,
    todos,
    AddTodo
  },
  
  data() {
    return {
      todos: []
    }
  },
  methods:{
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id !== id)
    },
    addTodo(newTodo){
      this.todos = [...this.todos, newTodo]
    }
  }
}
</script>

<style lang="sass">
  * 
    box-sizing: border-box
    text-align: center
  #app
    width: 500px
    margin-left: 300px
</style>
