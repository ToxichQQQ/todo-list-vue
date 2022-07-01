<template>
<div class="filter-panel">
  <div class="radio-group">
    <input id="all-radio" type="radio" name="all" value="all" @click="changeFilter">
    <label for="all-radio" v-bind:class="{active: isAll}">All</label>
  </div>
  <div class="radio-group">
    <input id="completed-radio" type="radio" name="completed" value="completed" @click="changeFilter">
    <label for="completed-radio" v-bind:class="{active: isCompleted}">Completed</label>
  </div>
  <div class="radio-group">
    <input id="uncompleted-radio" type="radio" name="uncompleted" value="uncompleted" @click="changeFilter">
    <label for="uncompleted-radio" v-bind:class="{active: isUncompleted}">Uncompleted</label>
  </div>
</div>
</template>

<script>
export default {
  name: "FilterPanel",
  props:{
    currentFilter: String
  },
  methods:{
    changeFilter(event){
        this.$emit('change-filter',event.target.value)
    },
  },
  computed:{
    isAll: function (){
      return this.currentFilter === 'all'
    },
    isCompleted: function (){
      return this.currentFilter === 'completed'
    },
    isUncompleted: function (){
      return this.currentFilter === 'uncompleted'
    }
  }
}
</script>

<style scoped>
  .filter-panel{
    bottom: 10px;
    position: absolute;
    right: 25%;
  }
  .radio-group{
    display: inline-block;
  }
  input[type='radio']{
    display: none;
  }
  label{
    border: 1px solid grey;
    cursor: pointer;
    padding: 0 15px;
  }
  .active{
    color: white;
    background-color: #41b883;
  }
</style>