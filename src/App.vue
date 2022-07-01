<template>
  <div class="todoList">
  <img class="img" alt="Vue logo" src="./assets/logo.png">
  <TodoHeader msg="TodoList on Vue.js"/>
   <TodoForm @add-item="addItem"/>
  <TodoList v-bind:items="filteredArray" @remove-item="removeItem" @toogle-value="toogleValue"/>
    <FilterPanel @change-filter="changeFilter" v-bind:currentFilter="filter"/>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoForm from "@/components/TodoForm";
import TodoList from "@/components/TodoList";
import FilterPanel from "@/components/FilterPanel";

export default {
  name: 'App',
  data(){
    return {
      filter:'all',
      items:[
        {id:'1', text:'Сходить в магазин', isDone:true},
        {id:'2', text:'Купить пиво', isDone:false},
        {id:'3', text:'Убраться дома', isDone:false}
      ]
    }
  },
  watch:{
    filter:function (){
      console.log('cla')
    }
  },
  computed:{
    filteredArray: function (){
       if (this.filter === 'completed'){
         return this.items.filter(item => item.isDone)
       }

      if (this.filter === 'uncompleted'){
        return this.items.filter(item => !item.isDone)
      }
      return this.items
    }
  },
  components: {
    FilterPanel,
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
    },
    changeFilter(value){
      this.filter = value
      console.log(value)
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
  position: relative;
  width: 600px;
  height: 500px;
  margin: 0 auto;
  border-radius: 10px;
  padding: 20px;
  -webkit-box-shadow: 0px 0px 5px 2px rgba(65,184,131,1);
  -moz-box-shadow: 0px 0px 5px 2px rgba(65,184,131,1);
  box-shadow: 0px 0px 5px 2px rgba(65,184,131,1);
}
</style>
