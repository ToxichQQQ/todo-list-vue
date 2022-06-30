<template>
  <div class="todoList">
  <img class="img" alt="Vue logo" src="./assets/logo.png">
  <TodoHeader msg="TodoList on Vue.js"/>
   <TodoForm @add-item="addItem"/>
  <TodoList v-bind:items="this.items" @remove-item="removeItem" @toogle-value="toogleValue"/>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoForm from "@/components/TodoForm";
import TodoList from "@/components/TodoList";

export default {
  name: 'App',
  data(){
    return {
      state: true,
      items:[
        {id:'1', text:'Сходить в магазин', isDone:true},
        {id:'2', text:'Купить пиво', isDone:false},
        {id:'3', text:'Убраться дома', isDone:false}
      ]
    }
  },
  components: {
    TodoList,
    TodoHeader,
    TodoForm
  },
  methods:{
    removeItem(id){
      console.log(id)
      this.items = this.items.filter(item => item.id !== id)
    },
    toogleValue(id){
      this.items = this.items.map(item => item.id === id ? {...item,isDone: !item.isDone} : item)
    },
    addItem(todo){
      this.items = [todo,...this.items]
    }
  },
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
