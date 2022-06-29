<template>
  <div class="todoList">
  <img class="img" alt="Vue logo" src="./assets/logo.png">
  <TodoHeader msg="TodoList on Vue.js"/>
  <TodoForm/>
  <TodoList/>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoForm from "@/components/TodoForm";
import TodoList from "@/components/TodoList";

export default {
  name: 'App',
  components: {
    TodoList,
    TodoHeader,
    TodoForm
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
  margin-top: 60px;
}

.img {
  width: 100px;
}

.todoList {
  width: 600px;
  margin: 0 auto;
}
</style>
